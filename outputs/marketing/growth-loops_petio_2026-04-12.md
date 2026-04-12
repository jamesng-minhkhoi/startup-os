# Petio — Growth Loops Analysis
**Date**: 2026-04-12  
**Scope**: AI Chat + Product Scanner (post-pivot features only)  
**Framework**: Ognjen Bošković — 5 Growth Loop Types

---

## TL;DR

The two pivot features — AI chat and product scanner — each have a distinct loop. Scanner is the **acquisition loop** (shareable content, viral in pet communities). AI chat is the **retention loop** (the more you use it, the better it gets, the harder it is to leave). Build the scanner viral mechanic before launch. Let AI chat compound over time on its own.

**Current Loop Score: 2/10** — neither loop has a mechanism to close yet  
**Ceiling with both loops live: 7/10**

---

## Loop Evaluation: All 5 Types for Petio's Pivot Features

| Loop Type | Fit | Rationale |
|-----------|-----|-----------|
| Viral (Scanner) | ★★★★★ | Scan results are inherently shareable — "this brand is unsafe for my dog" is social content |
| Usage (AI Chat Insights) | ★★★☆☆ | AI answers are shareable but require a share mechanic to close the loop |
| Referral | ★★★☆☆ | Works post-retention proof — not yet |
| Collaboration | ★★☆☆☆ | Out of scope for this phase |
| User-Generated | ★☆☆☆☆ | Requires social platform — not the product we're building |

---

## Loop #1 — Viral Loop via Product Scanner
**Fit: ★★★★★ | Status: Loop not closed | Build effort: Medium**

### Why the Scanner is the Viral Engine

The scanner creates one of the most shareable moments in consumer apps: discovering that a popular, trusted pet food brand has unsafe ingredients for your specific pet. This is not a "nice to have" moment — it's alarming, newsworthy, and highly social. People post this in Facebook pet groups, TikTok, and Zalo immediately.

The problem: the result lives inside the app with no exit. The loop has no closing mechanism.

### The Loop

```
User scans product barcode
        ↓
Safety result: "3 flagged ingredients for [pet name]"
        ↓
[MISSING] "Share result" → generates shareable card
        ↓
Card posted to: TikTok demo, Facebook pet group, Instagram story, Zalo
        ↓
Community members: "What app is that? How do I check my dog's food?"
        ↓
New users click CTA → App Store / Food Checker web tool → install
        ↓
New user scans their own product → gets their own share-worthy result
```

### The Shareable Card — Spec

What the card must contain to drive clicks:
- Product photo + name (pulled from barcode lookup)
- Large safety verdict: **"SAFE ✓"** or **"⚠ 3 FLAGGED INGREDIENTS"**
- Pet-specific line: "For [dog name] · [breed]" — proves AI personalization, not generic
- Top flagged ingredients listed by name (makes it concrete, not vague)
- "Checked by Petio · petiogo.com" badge — watermark, not hard sell
- Format: 9:16 optimized (TikTok/Stories) + 1:1 (feed)

### Vietnam Amplification

Vietnamese pet Facebook groups have 50K–500K members each and this is exactly the content they discuss. The scanner card hits the exact topic: "is [Vietnamese brand] safe for my dog?" Petio has the only personalized AI answer. Seeding 10 real scan results across major VN pet groups at launch (manual posts, community voice, no promotional copy) can drive a first spike of installs with zero ad spend.

**Key groups**: Hội nuôi chó mèo HCMC, allergy-focused dog groups (highest pain, most likely to share), Zalo pet communities.

**Content format that works**: Real scan on a popular Vietnamese brand (Ganador, Royal Canin VN, local treats). Not promotional — educational. Show the result, explain the flagged ingredients, let community engagement do the rest.

### Loop Coefficient (Vietnam estimate)

- % of users who scan and see a flagged result: ~50%
- % who share to a Facebook/Zalo group: ~15%
- Avg reach in VN pet group post: 500–2,000 views
- % who click and install from community post: ~2%
- **Net per share event: 10–40 installs**

One share = 10+ installs at the conservative end. This compounds fast in tight communities.

---

## Loop #2 — Usage Loop via AI Chat Insights
**Fit: ★★★☆☆ | Status: Partially closeable | Build effort: Low**

### Why AI Chat Can Close a Loop (With One Change)

The AI chat produces genuinely useful, personalized answers that users want to show other pet owners. "My AI vet told me my Golden's recurring ear infections are likely diet-related and suggested switching protein sources" is not a search result — it's a conversation. People screenshot these. The loop exists informally; it just needs a single share mechanic to formalize it.

### The Loop

```
User asks AI chat a question about their pet
        ↓
AI produces personalized, high-quality insight
        ↓
[ADD] "Share this answer" → generates insight card
        ↓
Card shows: question, AI answer excerpt, pet name/breed, "Answered by Petio AI"
        ↓
Shared in Reddit (r/dogs, r/cats), Facebook groups, friend DMs
        ↓
Viewers recognize personalization vs. generic Google results
        ↓
"How did you get a personalized answer like this?" → download
```

### What This Loop is NOT

This is not a user-generated content loop — pet owners aren't going to create public AI pet profiles for content creation. It's a much simpler usage loop: user gets value → has a natural urge to share the insight → sharing drives installs. The key friction is that there's currently no way to share. A "copy link" or "share card" button on any AI response closes it.

### Loop Coefficient (Lower than Scanner)

AI chat insights are less inherently alarming than a flagged scanner result — they're more likely to be shared in direct conversations than public groups. Lower reach per share, higher intent from the recipient. Useful for word-of-mouth, not viral spikes.

---

## Loop #3 — Referral Loop
**Fit: ★★★☆☆ | Status: Planned | Launch: Q3 2026**

"Give 1 month Plus, get 1 month Plus" — already in the roadmap. Hold until post-launch.

**Gate on**: D7 retention ≥ 25% from first 100-user cohort. Referral loops amplify existing behavior. If retention isn't there, you're incentivizing users to bring in churners.

---

## Key Metrics

### Scanner Viral Loop
| Metric | Target (90-day post-launch) |
|--------|----------------------------|
| % of scan sessions resulting in a share | 10% |
| Installs attributed to scanner share cards (UTM) | Track from day 1 |
| VN Facebook group posts / week (seeded) | 5–10 at launch |
| VN community-organic shares (not seeded) | Track from week 2 |

### AI Chat Usage Loop
| Metric | Target |
|--------|--------|
| % of AI sessions where user taps "share" | 5% |
| DM-attributed installs (referral code in share link) | Track via UTM |
| Reddit/community mentions of Petio AI | Monitor weekly |

---

## 30-60-90 Day Roadmap

### Days 1-30: Build the Scanner Viral Mechanic
- [ ] Design shareable scan result card (9:16 + 1:1) — Ngoc owns this
- [ ] Add "Share Scan" button to scanner results screen
- [ ] UTM tracking on all share links (platform + source)
- [ ] Build or update `/vi/tools/kiem-tra-thuc-an` as the web landing page for VN share traffic
- [ ] Write 5 seed posts for VN Facebook groups — real scan results on popular VN brands

### Days 31-60: Seed and Measure
- [ ] Post 1–2 scanner result demonstrations per week in top 5 VN pet Facebook groups
- [ ] Add "Share this answer" button to AI chat responses
- [ ] Monitor which flagged ingredients/brands drive the most shares and reshares
- [ ] US equivalent: seed 3–5 Reddit posts (r/dogs, r/cats, r/petadvice) with AI chat insight cards

### Days 61-90: Optimize and Layer
- [ ] A/B test card designs (alarming headline vs. informational headline)
- [ ] If D7 retention ≥ 25%: activate referral loop (RevenueCat promo codes)
- [ ] Identify top-converting scanner categories → brief Ngoc on content for TikTok scanner demo format
- [ ] VN: find 3–5 early power users in communities to turn into organic advocates

---

## Loop Stack Summary

```
NOW (Pre-Launch)
└── Build Scanner Viral Mechanic
    Shareable card + share button
    Build time: 3–5 days

LAUNCH (June 14)
└── Scanner Viral Loop LIVE
    Seed VN Facebook/Zalo groups
    Seed US Reddit pet communities

POST-LAUNCH (Q3 2026)
└── AI Chat Usage Loop (share button)
└── Referral Loop (if retention proven)
```

The scanner loop drives acquisition spikes. The AI chat loop builds slower but creates deeper word-of-mouth. Together they cover the full funnel from "cold discovery" to "this app is so good I had to tell my friend."
