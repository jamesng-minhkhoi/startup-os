# US / Global Launch Plan
**Last updated**: 2026-04-12 | **Launch date**: June 14, 2026

---

## Blockers — Nothing Ships Until These Are Done

| Blocker | Owner | Why it matters |
|---------|-------|---------------|
| Analytics events (scanner, chat, paywall, activation) | James | Can't measure or optimize anything post-launch |
| UTM referral tracking on all share links | James | Can't attribute installs to channels |
| 10 EN blog posts live | James | SEO needs runway before launch |
| Scanner share card built | James + Ngoc | Primary viral mechanic — must ship on launch day |
| Product Hunt ship page live | James | Must go live 2 weeks before June 14 |
| ASO: App name, keywords, screenshots (scanner-led) | James + Ngoc | First impression for every organic install |

---

## Channels

| Channel | Format | Owner | Cadence |
|---------|--------|-------|---------|
| **TikTok / Reels** | "Is This Safe?" — scan a popular US pet food, show the result. No voiceover needed. Hook: "I scanned the #1 selling dog treat in America." | James | 4–5/week pre-launch |
| **Reddit** | r/dogs, r/dogallergies, r/rawpetfood — be genuinely helpful for 2–3 weeks first, then introduce Petio as "a thing I built" | James | 30 min/day |
| **Facebook allergy groups** | Dog allergy/sensitivity groups — same trust-first approach as Reddit | James | 15 min/day |
| **SEO blog** | 10 posts targeting "can my dog eat X", "dog food scanner", "dog food allergy" — scanner CTA on every post | James | 2/week pre-launch |
| **ASO** | App name: "Petio — Dog Food Scanner & Pet AI". Lead screenshots with scanner. | James | One-time + monthly tune |
| **Micro-influencers** | Free Plus account for 60-day review — pet TikTokers with 10K–100K US followers. No cash. If they want ongoing, offer 25% rev share. | Vy | 5–10 creators, confirmed before launch |
| **Product Hunt** | Full launch June 14 — pre-build hunter network, collect upvotes day-of | James + Ngoc | One-time |

---

## Content That Works

**"Is This Safe?" format (TikTok/Reels)**
1. Pick a popular, trusted brand (Milk-Bones, Beggin' Strips, Blue Buffalo)
2. Scan with Petio on camera — no voiceover
3. Show the result, especially if something is flagged
4. Caption: "[brand] + [your dog's breed] = ?"

**What NOT to create:**
- Generic "10 tips for pet parents" listicles
- Founder story / meet the team
- Pet photo contests
- Any content that makes medical diagnosis claims

---

## Pre-Launch Checklist

**James**
- [ ] Analytics events instrumented (activation, scanner, chat, paywall, conversion)
- [ ] UTM tracking on all share links
- [ ] 10 EN blog posts live pre-launch
- [ ] Scanner share card built (see [feature spec](../product/features/08-scanner-share-card.md))
- [ ] Product Hunt ship page live (open 2 weeks before June 14)
- [ ] ASO: updated app name, description, screenshots (scanner-first)

**Vy**
- [ ] 5 US micro-influencers confirmed (free Plus for 60-day review)
- [ ] Reddit seeding started (2–3 weeks of genuine engagement before launch)
- [ ] Facebook dog allergy groups joined and active

**Ngoc**
- [ ] Scanner share card designed — 9:16 and 1:1 (see [spec](../product/features/08-scanner-share-card.md))
- [ ] Product Hunt graphics: logo, banner, demo GIF
- [ ] Updated App Store screenshots — scanner-first

---

## Launch Week Schedule

| Day | Action |
|-----|--------|
| **Jun 14** | Product Hunt live (need 50+ upvotes in first hour — activate personal network) |
| **Jun 14** | TikTok blitz — post 2 videos on launch day |
| **Jun 14** | Reddit: post "I built this" in r/dogs, r/dogallergies |
| **Jun 14** | All influencer content goes live simultaneously |
| **Jun 14–20** | All hands: respond to comments, App Store reviews, user reports |
| **Jun 21** | First metrics check — installs, early D7 retention signal |
| **Jul 14** | Launch +30 go/iterate/kill decision |

---

## What Success Looks Like at +30 Days

| Metric | Target | Below this → fix before scaling |
|--------|--------|---------------------------------|
| Total installs | 2,000+ | — |
| **Paying subscribers** | **100+** (5% of installs) | <50 = paywall or value problem |
| **US MRR contribution** | **$599+** | Combined with VN target: $1K total gross MRR |
| **Annual vs monthly mix** | **>20% annual** | Annual = $47.99 upfront vs $5.99/mo — push this hard |
| Day-7 retention | >25% | <15% = product problem, stop marketing |
| Free → Plus conversion | >5% | <2% = paywall problem — fix before scaling spend |
| AI chat sessions / active user / week | 3+ | <2 = core North Star, fix immediately |

**Combined target (US + VN)**: 100 US paying + 190 VN paying = ~$1,197 gross MRR. This is the $1K MRR milestone.

## Annual Subscription Strategy

Annual subscriptions are the fastest path to cash. 50 annual US subscribers = **$2,400 upfront** in one month vs $300/mo from 50 monthly subscribers.

**Paywall default must be annual**, not monthly. Monthly should look like the expensive option:
- Annual: $47.99/yr (~$4.00/mo) ← show this prominently
- Monthly: $5.99/mo ← show as the "flexible but pricier" option
- Add "Save 33%" badge on annual

This is a P1 fix before launch. Currently not confirmed in RevenueCat setup.

---

## If TikTok Underperforms (US Fallback)

TikTok is the primary US channel but results aren't guaranteed. If videos aren't hitting 10K+ views after 2 weeks, don't keep doing the same thing — shift:

| Fallback | What to do | Why |
|----------|-----------|-----|
| **Double Reddit/Facebook** | Increase from 30 min/day to 2 hrs/day. Go deeper in r/dogallergies and r/rawpetfood — answer every question, build credibility, soft-introduce Petio. | Allergic dog owner community is highly engaged, text-based, and underserved by video content. |
| **ASO push** | Optimise App Store for "dog food scanner" — if organic TikTok fails, search is the next best free channel. | At launch, ASO drives 40–60% of organic mobile installs for utility apps. |
| **Scanner share loop** | Focus energy on getting the share card into users' hands — every share reaches pet-owner friends organically. This compounds without any channel investment. | Scanner loop is product-native and doesn't depend on TikTok or social following. |

The $1K MRR target doesn't require TikTok virality — it requires 100 paying US users. Reddit + ASO + scanner shares can get there, just more slowly.

---

## Primary Growth Mechanism: Scanner Viral Loop

The most powerful US growth mechanic is not paid or earned — it's built into the product. When a user scans a product and shares their result, the share card reaches their pet-owner friends. This is the growth loop to optimize.

**Requirements for the loop to work:**
- Share card must be visually compelling (Ngoc)
- "Share this scan" must be a one-tap action post-scan (James)
- UTM links on every share so installs are attributed (James)

See [growth loops analysis](../../outputs/marketing/growth-loops_petio_2026-04-12.md) for full loop mechanics.
