# Petio 2026 Redesign — Sprint Plan

**Date:** 2026-04-26
**Source design:** Figma `TsGxXLXwYpb9Q0MJG0xIBf` ("[EXTERNAL] PETIO 2026")
**Codebase:** petio-mobile (Expo 55, RN 0.83, Expo Router, Unistyles, Supabase, Zustand, Gemini)
**Sprint length:** 3 weeks
**Capacity:** 2–3 engineers
**Posture:** Refactor in place, quality over speed

---

## 1. Scope & Constraints

### What the Figma file actually contains
- 8 artboards on a single page — **all variants of the Home screen**.
- 2 production candidates:
  - `119:5314` — first-time user / empty state (richest spec, includes Peti hero + Suggested-for-you chip rail)
  - `92:2825` — returning user / populated state (10 pets, upcoming-reminder strip)
- 5 "Meomeo" frames are layout A/B studies — ignored for this plan.
- **No designs yet** for: Onboarding, Auth, Pet detail, Pet creation, Scan tab landing, Settings, Statistics, Documents, Families, Notifications, Memories, Paywall, Tiny Moments engine.

### Architectural decisions (locked)
| # | Decision | Implication |
|---|---|---|
| 1 | Two canonical Home variants: `119:5314` (empty), `92:2825` (populated) | Two-state Home implementation; ignore the 5 layout studies |
| 2 | New nav: 5 tabs — **Home / My Pet / Peti (center, prominent) / Scan / Memory** | Reminders tab dropped, Scan promoted to tab, center tab is Peti chat entry |
| 3 | Reminder CRUD screens **kept**, just remove the tab entry | Reminders reachable via deep-link / pet detail; no rewrite of CRUD UI |
| 4 | Home "Chat with Peti" is **hybrid** — chip prompts run inline (one-shot), input bar tap deep-links to `/assistant` | AssistantSlice stays where it is; one-shot wrapper is new |
| 5 | "Tiny Moments / Aww templates" — visual placeholder only in Sprints 0–2 | Card renders but tapping defers; full template engine = separate spec |

### Non-goals (this plan)
- Redesigning screens that have no 2026 design (Pet detail, Onboarding, Auth, etc.) — queued, not sized.
- Building the Tiny Moments template engine — needs spec (lockscreen widget? share image? home-screen widget?).
- Removing reminder data layer, scheduling, or push notifications.
- Backend migration of AI (still client-side Gemini until told otherwise).

---

## 2. Net-New Surfaces vs Existing Code

| Surface | Status | Maps to |
|---|---|---|
| Aurora/blob gradient background | **New primitive** | new `<AuroraBackground />` |
| Peti Hero card (gradient + smiley + copy) | **New** | new `<PetiHeroCard />` |
| Home Chat input bar (with mic/voice) | **New** | new `<HomeChatInputBar />` |
| Suggested-for-you chip rail | **New** | new `<SuggestedPromptChip />` + `<ChipRail />` |
| 3 quick-action cards (with badge) | **New** | new `<QuickActionCard badge?>` |
| Pet card v2 (next-vaccine countdown, pink heart) | **Replaces** existing PetCard | `<PetCardV2 />` — rebuild |
| Upcoming reminder strip (header) | **New** | new `<UpcomingReminderStrip />` — queries `reminders` |
| Tiny Moments template card | **New (placeholder)** | new `<AwwTemplateCard />` (visual only) |
| "Get Plus" header pill | **New** | new `<GetPlusHeaderCTA />` — RevenueCat trigger |
| 5-tab nav with prominent center | **Replaces** 4-tab CustomTabBar | Edit `app/(protected)/(tabs)/_layout.tsx` + `<CustomTabBar />` |
| Scan tab landing screen | **New** (lifts from assistant tool) | new `app/(protected)/(tabs)/scan.tsx` |

---

## 3. Sprint Plan

### Sprint 0 — Foundations (3 weeks)

**Goal:** Land design system updates + nav restructure. Nothing yet renders the redesigned Home, but every primitive needed for Sprint 1 is built and tested in isolation.

**Parallel streams:** A (design system), B (nav + scan), C (data prep).

#### Stream A — Design system (1 engineer, full sprint)
- [A1] Extract design tokens from Figma into `theme/tokens.ts`:
  - Aurora gradient color stops + blur primitive
  - Peti hero card gradient
  - "Aww!!!" badge color/border
  - Chip rail tokens (chip background, border, hover)
  - Pet card v2 tokens (pink heart accent, weight-pill background)
- [A2] Build `<AuroraBackground />` primitive (positioned absolute, opacity-aware, theme-aware).
- [A3] Build `<PetiHeroCard />` — gradient bg, smiley SVG slot, title + body slots, optional CTA.
- [A4] Build `<HomeChatInputBar />` — text input + mic icon + voice/keyboard toggle + onSend.
- [A5] Build `<SuggestedPromptChip />` + `<ChipRail />` (horizontal scroll, dismissible).
- [A6] Build `<QuickActionCard badge?>` — icon, title, optional badge slot.
- [A7] Rebuild `<PetCardV2 />` — photo, name, breed, age, weight, next-vaccine countdown, pink heart accent.
- [A8] Build `<UpcomingReminderStrip />` — pill + reminder text + countdown formatter.
- [A9] Build `<GetPlusHeaderCTA />` — pill, taps trigger RevenueCat paywall via `useFeatureAccess`.
- [A10] Storybook-style component playground page (route under dev-only) for QA/screenshot review.

#### Stream B — Nav + Scan (1 engineer, full sprint)
- [B1] Reshape `app/(protected)/(tabs)/_layout.tsx` to 5 tabs: Home / My Pet / Peti / Scan / Memory.
- [B2] Update `<CustomTabBar />` to support a prominent center tab (larger icon, raised treatment).
- [B3] Center "Peti" tab routes to `/assistant` (existing screen) — for now, simple deep-link.
- [B4] Remove Reminders tab entry; verify `/(reminders)/*` routes still reachable via direct path.
- [B5] Add Pet Detail → "Reminders" link that deep-links to existing `RemindersScreen` filtered to pet.
- [B6] Add `app/(protected)/(tabs)/scan.tsx` scaffold + `<ScanScreen />` skeleton (camera permission gate, empty UI).
- [B7] Lift `ProductScanner` tool logic into a service so both `/scan` tab and the assistant tool can use it (no UI change to assistant tool yet).

#### Stream C — Data prep (0.5–1 engineer, partial sprint)
- [C1] Audit `reminders` slice for "next vaccination" derivation logic — write a selector returning `{ pet, daysUntil, reminderType }` used by `<UpcomingReminderStrip />`.
- [C2] Audit `vaccinations` table — confirm a vaccination record has `next_due_date` or equivalent; add migration if missing.
- [C3] Add `useNextVaccination(petId | 'any')` hook on top of stores.
- [C4] Discovery: find a single-shot Gemini call wrapper for chip prompts (no streaming, returns plain text + optional widget). Spec'd, not built — built in Sprint 2.

#### Sprint 0 exit criteria
- All new primitives render in playground with Figma-matched visuals (compared frame-by-frame to `119:5314`).
- New tab bar shipped; existing app still works (Home screen unchanged content, just new nav shell).
- No regressions in CI, Biome, type-check.

---

### Sprint 1 — Home assembly (3 weeks)

**Goal:** Both Home states (empty + populated) ship behind a feature flag, rendered from new primitives, wired to the existing data layer.

#### Stream A — Empty/first-time state (matches `119:5314`)
- [1A1] New `<HomeHeroHeader />` — Pawrent greeting + GetPlus pill + bell.
- [1A2] Compose Home empty state: HeroHeader → AuroraBackground → PetiHeroCard → HomeChatInputBar → ChipRail (static suggested prompts) → 3 QuickActionCards (Scan / Document / Memories+Aww badge) → AwwTemplateCard → My Pets section (1 pet card or empty CTA).
- [1A3] Suggested-prompt chips render statically (5–6 hardcoded prompts from Figma); tap behavior = deep-link to `/assistant?prompt=<text>` (one-shot wiring lands in Sprint 2).
- [1A4] `AwwTemplateCard` taps show "Coming soon" toast.
- [1A5] My Pets carousel uses existing `petsSlice`; renders `<PetCardV2 />`.

#### Stream B — Populated state (matches `92:2825`)
- [1B1] Add `<UpcomingReminderStrip />` to populated header (uses `useNextVaccination` from Sprint 0).
- [1B2] Conditional rendering: pets.length > 0 → populated layout; else → empty.
- [1B3] My Pets multi-pet horizontal carousel (FlashList horizontal) with "+" and "→" controls.
- [1B4] `→` arrow navigates to `/(pets)` (existing list screen).

#### Stream C — Wiring + observability
- [1C1] Feature flag `home_v2` (driven by RevenueCat or env). Existing HomeScreen kept; flag toggle swaps.
- [1C2] Track Home v2 events: `home_v2_viewed`, `peti_chip_tapped`, `peti_input_focused`, `quick_action_tapped` (action name), `pet_card_tapped`.
- [1C3] Empty-state instrumentation (so we can measure how often each path is exercised post-launch).
- [1C4] Performance baseline (TTI, scroll FPS) on iPhone 12 + low-end Android.

#### Sprint 1 exit criteria
- Home v2 (both states) shippable behind flag.
- Pixel parity check vs Figma at ≥90% on 6 key sections.
- No FPS regressions; cold-start TTI within 10% of current Home.

---

### Sprint 2 — Peti integration, Scan tab, polish (3 weeks)

**Goal:** Home v2 ships to all users. Scan tab is real. Peti chips do something useful. Get Plus pill works.

#### Stream A — Peti hybrid behavior
- [2A1] One-shot Gemini wrapper in `services/AssistantService.ts` (`runOneShot(prompt, ctx) → { text, widget? }`).
- [2A2] Suggested-prompt chips → tap calls `runOneShot`, shows result in TrueSheet (`PetiQuickAnswerSheet`) with "Continue in chat" CTA.
- [2A3] `HomeChatInputBar` send button = deep-link to `/assistant` with input pre-filled (existing assistant flow). Voice button = inline voice capture → text → deep-link.
- [2A4] Voice integration: `expo-speech` recognition (iOS) + Android equivalent or fallback to keyboard.
- [2A5] Track: `peti_oneshot_succeeded`, `peti_oneshot_failed`, `peti_continue_to_chat`.

#### Stream B — Scan tab build-out
- [2B1] `<ScanScreen />`: camera viewfinder + barcode/object detection (reuse ProductScanner service from Sprint 0).
- [2B2] Recent scans list (Supabase: new `product_scans` table — small migration).
- [2B3] Scan result → opens `/assistant` with `ProductReport` widget pre-rendered (existing widget pipeline).
- [2B4] Empty state: "Point at a pet product to begin".
- [2B5] Settings: scan history clear, camera permission re-request.

#### Stream C — Reminders deprecation + polish
- [2C1] Pet Detail screen — add "Reminders" section linking to filtered `RemindersScreen`.
- [2C2] Remove `Reminders` from any tab/menu surface; verify all create paths still work (deep-links from notifications, from pet detail).
- [2C3] Update push notification deep-links to point at new Pet Detail → Reminders route.
- [2C4] `Get Plus` pill wired to RevenueCat paywall (existing `PaywallScreen`).
- [2C5] Accessibility pass on Home v2 (touch targets ≥44pt, VoiceOver labels, contrast vs aurora bg).
- [2C6] Visual regression baseline (Detox or Maestro snapshot tests on Home empty + populated).

#### Sprint 2 exit criteria
- Home v2 default-on; flag retained as kill switch.
- Scan tab usable; ≥80% scan-to-result success on test products.
- VoiceOver navigates Home v2 in correct order; no contrast failures.
- Reminder push notifications still deliver and deep-link correctly.

---

## 4. Sprint 3+ — Awaiting Design (Queue, Not Sized)

These screens are part of the Petio 2026 redesign but have no Figma yet. They are listed in priority order based on user impact and dependency on Home (highest first). **Do not size until designs land.**

| # | Surface | Dependency / Notes |
|---|---|---|
| 1 | Pet Detail screen | Most-used screen after Home; tabs (Care/Health/Details) likely consolidate or restructure |
| 2 | Pet creation wizard (13 steps) | Onboarding-adjacent; large surface area |
| 3 | Onboarding (welcome, slides, surveys, paywall) | First-run; recently refactored to typed step registry — visual update only? |
| 4 | Auth (login, sign-up, reset) | Low frequency but first impression; standalone |
| 5 | Statistics / health charts | Stats dashboard expansion — what's the new spec? |
| 6 | Memories detail + new memory | Tab still present; needs visual update to match Home |
| 7 | Documents library | Tab not present in new nav — does it become a sub-route? Decision needed |
| 8 | Families / sharing | Same as Documents — IA decision needed |
| 9 | Settings hub + sub-screens | Lowest urgency |
| 10 | Notifications center | Lowest urgency |
| 11 | Tiny Moments / Aww template engine | **Needs PRD before design** — what does it produce? |
| 12 | Pet search / filter | Currently TODO in code; can be net-new |

**Recommended action:** before Sprint 3 starts, hold a design review with these in priority order. Design 1–3 in parallel; sprint 3 picks up the first one ready.

---

## 5. Cross-Cutting / Always-On Tracks

These run alongside every sprint, owned across the team:

- **Design system stewardship.** As primitives land, document in a UI library page; deprecate old equivalents (don't delete until all consumers migrated).
- **Migration sweep.** Existing screens still using legacy `AppCard`/`PetCard` get migrated to v2 components incrementally — opportunistic, not forced.
- **Test coverage.** Unit tests for new primitives; integration tests for Home v2 states; E2E for critical paths (open app → see Home → tap quick action → return).
- **Visual regression.** Baselines locked at end of Sprint 1; CI gate from Sprint 2 onwards.
- **Performance budget.** Home cold start, scroll FPS, image load timing tracked per release.
- **Accessibility audit.** Per-sprint VoiceOver + contrast pass on shipped surfaces.

---

## 6. Risks & Open Questions

| Risk / Question | Severity | Mitigation |
|---|---|---|
| Tiny Moments has no spec — could become a quarter of work if descoped late | High | Treat as placeholder; force a spec doc before sizing |
| Voice input on Android may need a different package than iOS | Medium | Spike in Sprint 0 Stream C; fallback to text-only on Android if blocked |
| One-shot Gemini latency on Suggested chips may feel slow | Medium | Add optimistic UI ("Peti is thinking..."), measure p95 in Sprint 2 |
| Aurora background may tank low-end Android FPS | Medium | Use static image fallback below an FPS threshold; measure in Sprint 1 exit |
| Reminders deep-links from push notifications may break during nav restructure | High | Sprint 0 [B4]: explicit verification; release notes flag if behavior changes |
| Center "Peti" tab feels like nav, but is a deep-link destination — UX confusion | Low | If post-Sprint-2 telemetry shows confusion, swap to floating FAB |
| Design for next surfaces (Pet detail, Onboarding) lands mid-Sprint-2 and pulls focus | Medium | Designer commits to delivery cadence; engineering does not start Sprint 3 work until Sprint 2 ships |

---

## 7. Definition of Done (per sprint)

A sprint is done when:
1. All exit-criteria items verified by demo.
2. CI green: type-check, Biome, unit tests, gitleaks, type drift.
3. Performance baseline within budget (no regressions ≥10%).
4. Accessibility checks pass on shipped surfaces.
5. Code reviewed and merged to `main`.
6. TestFlight build distributed.

---

## 8. Backlog of Decisions for the User/Designer

Record these so they're not lost between now and Sprint 3:

1. **What is "Tiny Moments / Aww templates"?** Lockscreen widget? Shareable image? Home-screen widget? Defines whether it's a 2-week feature or a quarter.
2. **Documents and Families — where do they live in the new IA?** Not in the 5-tab nav. Sub-route under Settings? Pet Detail tab? Profile?
3. **Pet creation wizard — keep 13 steps or compress?** Opportunity during redesign.
4. **Onboarding visual refresh — full redesign or token-update only?** It was just refactored; cheap to restyle.
5. **Statistics — expand to be a primary tab, or keep as deep-link from Pet Detail?** Currently no design.
6. **Center tab name and behavior** — confirmed "Peti" for now. Long-term: is this where AI lives, or does it grow to be more (assistant + scan)?
