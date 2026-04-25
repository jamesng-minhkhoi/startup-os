# Petio AI Feature — Research & Implementation Plan

**Date:** 2026-04-26
**Author:** James + Claude (research session)
**Status:** Research / pre-build hardening
**Scope:** Hardening the built AI Chat + Product Scanner via Supabase Edge Function migration
**Aligned to:** `docs/product/features/03-ai-chat.md`, `04-product-scanner.md`, `05-memories.md`, `10-documents.md`

> **Important framing:** AI Chat and Product Scanner are **already built and shipping** on `gemini-2.0-flash` directly from the client. This doc is about (a) closing the spec'd P1 gaps (allergen context, rate-limit UI, "Report incorrect result", dead buttons) and (b) migrating the AI surface behind a Supabase Edge Function proxy so we can ship to production safely. It is **not** a greenfield rebuild.

---

## Table of Contents
1. [Current Stack Snapshot](#1-current-stack-snapshot)
2. [Production Architecture (Edge Function Proxy)](#2-production-architecture-edge-function-proxy)
3. [AI Chat — Orchestration Design](#3-ai-chat--orchestration-design)
4. [AI Chat — End-to-End Scenarios](#4-ai-chat--end-to-end-scenarios)
5. [Product Scan Feature](#5-product-scan-feature)
6. [Proposed Answers to Spec Open Questions](#6-proposed-answers-to-spec-open-questions)
7. [Open Decisions](#7-open-decisions)

---

## 1. Current Stack Snapshot

**petio-mobile already has:**
- Expo SDK 55, RN 0.83, React 19
- Supabase (auth, Postgres, storage)
- RevenueCat (subscriptions — Free / Plus tiers)
- `@google/generative-ai` (Gemini 2.0 Flash) wired into `services/AssistantService.ts`
- Function-calling tool definitions for: `render_product_report`, `render_health_chart`, `render_generic_info`, `render_pet_profile`
- `@`-mention system in chat for pets and documents
- API key currently shipped client-side via `EXPO_PUBLIC_GEMINI_API_KEY`
- No Supabase Edge Functions yet

**Reference architecture available:** `app_child_development/supabase/functions/api/` — Hono + OpenAPI + JWT auth middleware + typed Supabase clients + tested routes. Mirror this pattern.

**Spec'd P1 gaps to close as part of this work:**
- AI Chat: allergen context in prompt, health-condition context, error states, rate-limit UI
- Scanner: allergen-aware analysis, "Product not found" prompt, wire dead buttons (Full Report, Find Alternatives), "Report incorrect result", `scan_history` table

---

## 2. Production Architecture (Edge Function Proxy)

### Why migrate off client-direct Gemini

- API key in client bundle = anyone can extract → cost/abuse risk
- No per-user rate limiting (Free 5 chats/day + 3 scans/day cannot be enforced server-side)
- No server-side entitlement gating (jailbroken client bypasses RevenueCat)
- Can't swap models without an app update
- No request logging / cost tracking

### Target architecture

```
RN app  ──HTTPS+JWT──▶  Supabase Edge Function (Deno + Hono)
                            │
                            ├── verify JWT (supabaseUser client)
                            ├── check entitlement (RevenueCat → subscriptions table)
                            ├── enforce quota (Postgres counter — Free: 5 chats / 3 scans / day)
                            ├── load context (pet data + @mentioned docs via supabaseAdmin)
                            ├── call LLM (Gemini 2.0 Flash — primary)
                            ├── log request+tokens to llm_requests table
                            └── stream SSE response back
```

### Tech choices

| Layer | Pick | Why |
|---|---|---|
| Runtime | Supabase Edge Functions (Deno) | Already in stack; sibling proves pattern |
| HTTP framework | Hono + `@hono/zod-openapi` | Matches sibling; Swagger + Zod validation free |
| LLM (primary) | **Gemini 2.0 Flash** | Per spec — already built on it; tool-calling + vision; cheap |
| LLM (future option, not committed) | Claude Sonnet 4.6 / 5.x | Stronger tool-use + prompt caching; reconsider post-launch if quality issues surface |
| SDK in function | `npm:@google/generative-ai` | Same SDK as client today, port over |
| Streaming to RN | SSE over `fetch` w/ `ReadableStream` | RN 0.83 + React 19 supports it |
| Auth | Existing Supabase JWT | Same as sibling's `lib/auth.ts` |
| Entitlement gate | RevenueCat REST webhook → `subscriptions` table | Server-side, can't be bypassed |
| Secrets | `supabase secrets set GEMINI_API_KEY=…` | Never in client bundle |
| Rate limiting | Postgres `usage_quota` table per (user, day, kind) | Free, good enough; powers "2 messages left today" UI |
| Observability | `llm_requests` table (user_id, kind, model, tokens, cost, latency) | Per-user cost visibility |
| Caching | Cache pet context + system prompt server-side per request | Cuts repeated token cost |

### Migration phases

**Phase 0 — Foundations (1–2 days)**
- Init `supabase/config.toml` + `functions/api/` skeleton mirroring sibling
- Port `lib/auth.ts`, `lib/response.ts`, error envelope shape
- Set secrets, deploy `/health` endpoint, verify JWT round-trip from app

**Phase 1 — Move existing assistant + scanner (2–3 days)**
- New endpoint `POST /api/assistant/chat` (streaming SSE)
- New endpoint `POST /api/scanner/analyze` (barcode + optional pet_id)
- Move tool declarations + system prompt from `services/AssistantService.ts` into the edge function
- Refactor client `AssistantService` to a thin fetch wrapper
- Implement `usage_quota` + `llm_requests` + `scan_history` tables
- Delete `EXPO_PUBLIC_GEMINI_API_KEY` from app
- Rotate the old key (it's been in shipped builds)

**Phase 2 — Close spec'd P1 gaps (2–3 days)**
- Allergen + health-condition context injection into prompt (depends on `pets.allergies`, `health_conditions`, `current_medications` fields landing first)
- Rate-limit UI: server returns `quota_remaining` in every response → client shows "2 messages left today"
- "Report incorrect result" endpoint + Supabase storage table for review
- "Product not found" UX path (server returns `unknown` verdict + manual entry flow)
- Wire dead buttons: "Full Report" view + "Find Alternatives" follow-up message

**Phase 3 — Post-launch (P2 in spec)**
- Open Pet Food Facts integration to improve scanner accuracy (replaces LLM-only barcode lookup)
- Conversation history cloud sync (today: device-only via AsyncStorage)
- Share-this-answer card

**Architecture choice:** one mega edge function (`api`) like sibling — easier shared middleware, single cold start.

---

## 3. AI Chat — Orchestration Design

### Core decision: single-call with tool use (vs. router-first)

Recommended: **single-call with tools.** One LLM call per turn. Model sees user message + system prompt + tool definitions and decides which tools to invoke. Add a router-first pattern only if real-world safety failures require it.

### Tool design (the three core scenarios)

```js
tools = [
  {
    name: "get_pet_data",
    description: "Retrieve detailed info about one of the user's pets — health logs, weight history, allergies, vaccinations, recent reminders. Use whenever the user asks about a specific pet, references 'my dog/cat', or asks anything that needs context about a specific animal.",
    input_schema: { pet_id, fields[]: ["weight_history","allergies","reminders",…] }
  },
  {
    name: "lookup_product",
    description: "Look up a pet food/treat/medication by barcode, brand+name, or photo. Returns ingredients, recalls, known allergens. Use when the user asks if something is safe, mentions a brand, or provides a product image/barcode.",
    input_schema: { barcode?, brand?, product_name?, image_url? }
  },
  {
    name: "escalate_to_vet",   // PROPOSED — answers spec open question
    description: "MUST be called when the user describes any of: severe symptoms (vomiting blood, seizure, collapse, breathing distress, ingestion of toxic substance, suspected poisoning, severe injury), behavior change suggesting acute illness, or anything where delay could cause harm. Returns a vet-escalation message. After calling this you MUST NOT continue medical reasoning in the same turn.",
    input_schema: {
      severity: "emergency"|"urgent"|"see-vet-soon",
      reason: string,
      suggested_action: string
    }
  }
]
```

The `escalate_to_vet` tool is the safety lever — when called, the edge function intercepts the result and returns a deterministic UI (red banner, find-vet CTA, emergency hotline). The model never gets to "talk past" the escalation. **This is a proposed answer to spec open question: "Should the AI proactively suggest a vet visit?"**

### `@`-mention context injection (per spec P0)

The chat already supports `@PetName` and `@DocumentName` mentions. In the edge function flow, mentions are resolved server-side **before** the LLM call:

```
1. Parse user message → extract @mentions
2. For each @PetName: load full profile (allergies, conditions, vaccinations) via Supabase
3. For each @DocumentName: load document text via Supabase storage
   - If PDF/image: OCR via Gemini Vision into plain text first
   - Cache extracted text on the document row to avoid re-OCR
4. Inject as a structured context block in the LLM prompt:
   "[Mentioned pet: Luna — Golden Retriever, 3yo, allergies: chicken, wheat]
    [Mentioned document: VaccinationRecord_Luna.pdf — <extracted text>]"
5. Continue to tool-use loop
```

**Why server-side, not via tool call:** the user explicitly tagged these — no need to make the model "decide" to fetch. Saves a round-trip and is more reliable than hoping the model calls `get_pet_data` for `@Luna`.

The `get_pet_data` tool stays for inferred references ("my dog", "Bella" without `@`).

### Safety: defense in depth

Don't rely on one mechanism. Stack them:

1. **System-prompt rules** — cheap, sometimes ignored under pressure
2. **`escalate_to_vet` tool** — model is much better at "called the right tool" than "followed paragraph rules"
3. **Pre-call regex/keyword tripwire** for unmissable cases ("seizure", "blood", "not breathing", "ate chocolate", "ate xylitol/grapes/onion") — skip the LLM entirely, return escalation card
4. **Post-call validator (optional)** — second cheap LLM call to flag dosage/diagnosis content; replace with safe fallback
5. **Persistent disclaimer** in every medical-adjacent response card

The tripwire (3) + tool (2) is the 80/20.

### Intent detection without a separate classifier

**Tool descriptions ARE your intent classifier.** Write descriptions like routing rules. The model picks tools based on description matching. Iterate on descriptions, not on prompt rules.

### Tool-call loop

```
async function chat(userMessage, userId, conversationId):
  // 1. Cheap safety net
  if (tripwireMatches(userMessage)):
    return EMERGENCY_RESPONSE

  // 2. Resolve @mentions server-side (pets + documents)
  contextBlock = await resolveMentions(userMessage, userId)

  // 3. Load conversation history (last 50 per spec)
  messages = await loadHistory(conversationId, 50)
  messages.append({ role: "user", content: contextBlock + userMessage })

  // 4. Tool-use loop (max 4 turns)
  for i in range(4):
    response = await gemini.generateContent({
      model: "gemini-2.0-flash",
      systemInstruction: SYSTEM_PROMPT,
      tools: TOOLS,
      messages
    })

    if response.stop_reason == "end_turn":
      await saveHistory(...)
      return response.text + widgetCalls

    if response.stop_reason == "tool_use":
      for toolCall in response.tool_calls:
        // SAFETY SHORT-CIRCUIT
        if toolCall.name == "escalate_to_vet":
          return buildSafetyResponse(toolCall.input)

        // NORMAL DATA TOOL
        result = await runTool(toolCall.name, toolCall.input, userId)
        messages.append(response)
        messages.append({ role: "tool_result", content: result })
        // loop, model sees result, decides next step

  return FALLBACK_RESPONSE  // never infinite loop
```

**~80 lines of code total** plus the mention resolver. Tripwire + 3 tools + the loop.

### System prompt skeleton

```
You are Petio, an assistant for pet owners. You have tools to retrieve
pet data and look up products. You are NOT a vet.

SAFETY RULES (non-negotiable):
1. If the user describes any acute medical situation (poisoning, seizure,
   collapse, severe bleeding, breathing distress, sudden behavior change
   suggesting illness), call escalate_to_vet IMMEDIATELY before any
   other tool.
2. Never give specific drug dosages, diagnoses, or "wait and see" advice
   for symptomatic pets. Recommend a vet.
3. For product safety: use lookup_product, then cross-reference with the
   pet's allergies via get_pet_data (or use the @mention context block
   if pet was tagged).

TOOL USE:
- For inferred pet references ("my dog", "Bella"), use get_pet_data.
- For @mentioned pets/documents, use the context block already injected.
- After any tool call, give a 1–2 sentence natural-language summary
  alongside the rendered widget.

CURRENT USER: {user_id}, has {n} pets registered.
```

---

## 4. AI Chat — End-to-End Scenarios

Same code path; different inputs, different outcomes.

### Scenario 1: Casual chat — no tools

User: *"Hi! What's a fun toy for my cat?"*

```
[1] Tripwire: no match
[2] No @mentions
[3] Gemini call → end_turn: "Cats love wand toys, puzzle feeders..."
```
1 LLM call. UI: plain chat bubble.

### Scenario 2: Pet-specific question via @mention

User: *"Is @Bella due for vaccines?"*

```
[1] Tripwire: no match
[2] @Bella resolved → loads Bella's profile + vaccinations
    Context injected: "[Mentioned pet: Bella — rabies last 2025-03-10, due 2026-03-10]"
[3] Gemini call → end_turn:
    "Bella's rabies is overdue (due Mar 10, 2026). Book a vet visit this week."
    + render_pet_profile widget
```
1 LLM call + 1 DB query. UI: chat bubble + vaccination card with "Book vet" CTA.

### Scenario 3: Product safety with @ pet — chained tools

User: *"Can I give @Rocky this Blue Buffalo treat?"* + photo

```
[1] Tripwire: no match
[2] @Rocky resolved → allergies: ["wheat", "soy"] injected as context
[3] Gemini #1 (with image + context) → tool_use: lookup_product { brand, image_url }
[4] Edge runs lookup → ingredients: ["chicken","wheat","oat"...]
[5] Gemini #2 → end_turn: "Heads up — contains wheat and Rocky is allergic. Skip it."
    + render_product_report (status: "unsafe")
```
2 LLM calls. Allergen check happens because mention pre-loaded the context.

### Scenario 4: Document @mention

User: *"@VaccinationRecord — when is Luna's next booster due?"*

```
[1] Tripwire: no match
[2] @VaccinationRecord resolved → load PDF from Supabase storage
    If no cached text: Gemini Vision OCR → cache on document row
    Inject: "[Mentioned document: <extracted text>]"
[3] Gemini call → end_turn with parsed answer
```
1–2 LLM calls (depending on OCR cache hit).

### Scenario 5: Emergency — tripwire short-circuit

User: *"My dog ate chocolate help"*

```
[1] Tripwire: "chocolate" found in EMERGENCY_TERMS
    ⚡ SHORT CIRCUIT — never call Gemini
[2] Return canned safety response with hotline + find-vet CTAs
```
0 LLM calls. Instant. No way for the model to mess this up.

### Scenario 6: Subtle emergency — model catches it

User: *"My cat has been throwing up all day and seems really weak"*

```
[1] Tripwire: no match
[2] Gemini #1 → tool_use: escalate_to_vet { severity: "urgent", reason: "..." }
[3] Edge sees escalate_to_vet → SHORT CIRCUIT, do NOT continue loop
[4] Return safety response with find-vet CTA
```
The model wanted to keep talking — code didn't let it.

### Build order (post-edge-function migration)

| Day | Deliverable |
|---|---|
| 1 | Skeleton + Scenario 1 (basic chat through edge fn) |
| 2 | @mention resolver + Scenarios 2/4 |
| 3 | Tripwire + Scenario 5 |
| 4 | escalate_to_vet tool + Scenario 6 |
| 5 | lookup_product + Scenario 3 |

---

## 5. Product Scan Feature

### Spec-aligned launch path (LLM-only barcode lookup)

Per `04-product-scanner.md`: **at launch, scanner identifies product entirely via Gemini inference from the barcode value. No third-party DB.** Known accuracy risk is mitigated by a "Report incorrect result" button. Open Pet Food Facts is **post-launch (P2)**.

```
Launch flow:
  barcode → Gemini (identify product + extract ingredients) → score → render widget
            └── if not found → "Product not found" prompt → manual entry
```

### Personalization is the differentiator (P1 — must close)

Same product scores differently per pet based on `pets.allergies` (and `health_conditions`, `current_medications` once those fields land):

- Pet has chicken allergy + product has chicken → **UNSAFE** (hard rule)
- Pet overweight + product high-fat → caution penalty
- Pet senior + product is puppy formula → caution penalty
- Pet has kidney issues + high-phosphorus → unsafe penalty

This is the moat. Without it, we're a generic ingredient lookup.

### Suggested scoring formula (NEW — spec doesn't define one)

Adapt **Yuka's transparent model**. Final output stays as the spec'd 3-state widget: **Safe / Caution / Unsafe**.

#### Step 1 — Hard rules (override everything)

```
if any ingredient ∈ TOXIC_TO_SPECIES(pet.species):
    → UNSAFE, stop
    (xylitol, chocolate, grapes for dogs;
     onion, garlic, propylene glycol for cats)

if any ingredient matches pet.allergies:
    → UNSAFE, reason="contains your pet's allergen: X"

if species mismatch (dog food, pet is cat):
    → UNSAFE, reason="dog food lacks taurine cats need"
```

(FDA recall list check moves in once we add OPFF post-launch.)

#### Step 2 — Weighted score (when no hard rule fires)

Start at **100**. Apply additive deltas. Map to verdict bands.

| Component | Weight | How it scores |
|---|---|---|
| **Ingredient quality** | ±40 | +40 if first 3 ingredients are named meats. 0 if first is grain. −20 if "meat by-products" or "animal digest" in top 5. −10 if "meat meal" generic (unnamed). |
| **Protein content** | ±15 | Compare guaranteed-analysis protein % to species/life-stage AAFCO minimum. Hit min: 0. Exceed by 5pp: +10. Below min: −15. |
| **Controversial additives** | −5 each (cap −25) | BHA, BHT, ethoxyquin, propylene glycol (cats), artificial colors, added sugar, MSG, carrageenan. |
| **Filler ratio** | ±10 | Counts of corn/wheat/soy/by-products in first 5. None: +10. 3+: −10. |
| **AAFCO life-stage** | ±10 | Statement matches pet's life stage: +10. None: −10. |
| **Manufacturer transparency** | +5 | Lists manufacturing country + facility. |

#### Step 3 — Map to verdict

```
score ≥ 70  → SAFE     (green)
40 ≤ < 70   → CAUTION  (yellow)
score < 40  → UNSAFE   (red)
```

Always show top 2–3 reasons. Spec is open on whether to show the numeric score itself — see Open Decisions.

### Where the LLM fits

**Don't ask the LLM "is this safe?"** — that's how you get hallucinated medical advice.

Use the LLM only for **deterministic data extraction** and **plain-English explanation**:

```
1. Identify product + extract ingredients   (LLM — Gemini)
2. Score = run formula on JSON               (pure code, unit-testable)
3. Explain score in friendly language        (LLM — Gemini)
```

Scoring is **unit-testable** — same product + same pet = same score, every time.

### Closing the spec'd dead buttons + gaps

| Spec gap | Implementation |
|---|---|
| `scan_history` table (barcode, product_name, status, scanned_at, pet_id) | New Postgres table, populated on every scan, RLS by user_id, capped at last 10 per pet |
| "Report incorrect result" | New endpoint `POST /api/scanner/report` → writes to `scan_reports` table for human review |
| "Product not found" prompt | When Gemini cannot identify barcode → return `{ verdict: "unknown" }` → client opens manual-name entry sheet |
| "Full Report" button | Renders full extracted ingredient list + per-ingredient flag reasons in chat detail view |
| "Find Alternatives" button | Sends an AI follow-up message: "Find safer alternatives to {product_name} for {pet_name}" — uses normal chat path |

### Concrete data flow (launch — LLM-only)

```
[Scan barcode]
        │
        ▼
  Cache hit on (barcode, pet_id) within scan_history?  ──yes──▶ return cached
        │ no
        ▼
  Gemini: identify product + extract ingredients from barcode
        │
        ├── could not identify? ──▶ return { verdict: "unknown" } → manual entry UI
        │
        ▼
  Score formula (pure function: product + pet)
        │
        ▼
  Gemini: write 2-sentence explanation from score breakdown
        │
        ▼
  Save to scan_history (user_id, pet_id, barcode, product_name, verdict, score, scanned_at)
        │
        ▼
  Return widget data → render_product_report card
```

### Post-launch (P2): OPFF integration

- Add Open Pet Food Facts as Tier-1 lookup before LLM inference (~50% hit rate, free)
- LLM inference becomes Tier-2 fallback
- Add FDA recall cross-reference (free, public dataset, sync monthly)
- Cuts hallucination risk + scan latency

---

## 6. Proposed Answers to Spec Open Questions

These are **my recommendations** — flag for product/founder sign-off before building.

### From `03-ai-chat.md`

> *"Should the AI proactively suggest a vet visit for certain questions? And if so, how do we word it without it feeling like a liability disclaimer?"*

**Proposed:** Yes — implement via the `escalate_to_vet` tool (Section 3) with a deterministic safety card UI (find-vet CTA, emergency hotline) rather than the AI freeform-suggesting it. Two tiers: tripwire (deterministic, hotline) + model-called escalation (find-vet CTA + 24h advice). Wording focuses on action ("Book a vet visit today") not disclaimer ("This is not medical advice").

> *"Should message limit reset at midnight local time or midnight UTC?"*

**Proposed:** Local time. UTC creates "your messages reset at 7am" confusion for US users. Implementation: store user timezone on profile (already needed for reminders), bucket quotas by user-local date.

> *"Conversation history cloud sync?"*

**Proposed:** Post-launch (P2). Adds Supabase storage cost + sync conflict surface for a feature most single-device users won't notice.

### From `04-product-scanner.md`

> *"If a user has multiple pets, which pet's profile does the scanner check against?"*

**Proposed:** Last-selected pet, persisted across sessions. Add an inline "Switch pet" chip on the scan result card so users can re-evaluate the same scan against a different pet without re-scanning. Per-pet result is cached, so the toggle is instant.

> *"What's the right UI for 'this product is safe for Max but unsafe for Luna'?"*

**Proposed:** Single result card per scan (against currently-selected pet). Below the verdict, show a "Check for your other pets" row with each other pet's mini-verdict pill. Tapping a pill expands their full result. Avoids overwhelming the primary outcome.

> *"OPFF integration at launch or post-launch?"*

Spec already settled this: **post-launch (P2)**. This doc respects that.

---

## 7. Open Decisions

These need product/founder calls before build:

### Architecture
1. **Streaming required day-one?** — SSE adds complexity; non-streaming JSON is simpler if UX can wait 2–4s. Spec's <3s latency target is achievable either way.
2. **One mega edge function (`api`) or one per feature?** — Recommend mega, mirror sibling.
3. **Document OCR caching** — cache extracted text on the document row (faster, cheaper, but stale if user re-uploads) vs re-OCR on each mention (always fresh, costs $0.005/mention). Recommend cache + invalidate on re-upload.

### AI chat
4. **Tripwire keyword list scope** — draft full pet emergency list (chocolate, xylitol, antifreeze, lily for cats, etc.) — needs vet review before ship.
5. **Severity levels** — emergency / urgent / see-vet-soon (3-tier) vs simpler binary?
6. **Memory across turns for tool results** — re-fetch pet data each turn (safer, more tokens) or carry results in history (cheaper, can drift)?

### Product scan
7. **Score weights calibration** — pick 20 known products (5 great, 10 mid, 5 garbage), score by hand, tune weights to match before locking.
8. **Show numeric score or just the band?** — Yuka shows 0–100 + emoji; DogFoodAdvisor shows stars; spec is silent.
9. **"Report incorrect result" review workflow** — who triages reports? Auto-escalate after N reports?

### Production hardening
10. **Plus entitlement enforcement timing** — implement server-side quota immediately, or rely on client-side enforcement until Plus launches?
11. **Cost ceiling per user** — set hard cap, shut off + notify if exceeded?
12. **Health-condition + current-medications fields** — dependency on Pet Profiles P1; need ETA before AI Chat P1 work can start.

---

## Appendix A — File touch list (for build)

**New (edge function):**
```
supabase/
  config.toml
  functions/api/
    deno.json
    index.ts
    lib/{auth.ts, response.ts, gemini.ts, tripwire.ts, mentions.ts}
    routes/{assistant.ts, scanner.ts}
    tools/{get_pet_data.ts, lookup_product.ts, escalate_to_vet.ts}
    scoring/{formula.ts, hard-rules.ts, weights.ts, toxins.ts}
    tests/{assistant.test.ts, scoring.test.ts, tripwire.test.ts, mentions.test.ts}
```

**New (Postgres):**
```
migrations/
  YYYYMMDD_llm_requests.sql
  YYYYMMDD_usage_quota.sql
  YYYYMMDD_scan_history.sql        -- per spec field list
  YYYYMMDD_scan_reports.sql        -- "Report incorrect result"
  YYYYMMDD_subscriptions.sql       -- if not already present
```

**Modified (client):**
```
services/AssistantService.ts   ← becomes thin SSE fetch wrapper
.env                            ← remove EXPO_PUBLIC_GEMINI_API_KEY
screens/scanner/*               ← wire dead buttons, "Report incorrect", "Product not found"
```

**Deleted:**
```
(none — keep widget rendering components on client)
```
