# Petio Sprint Status — 2026-04-07

## What Was Completed (Apr 2-3)

### Mobile App (petio-mobile)

| Task | Detail |
|------|--------|
| **Codebase refactoring** | Split 5 mega-files (StatisticsScreen 1,686→127, CustomTabBar 776→160, ReminderForm 582→119, HomePetSection, authSlice 429→216+157+63) |
| **Duplication removal** | FileUploadService (consolidated 3 implementations), useCrudList (replaced 6 identical lists), getCurrentUserId (used in 16 slices), limits.ts (14 magic numbers) |
| **Design system** | shadowTokens, componentSizeTokens, StyleProps system, centralized haptics + motion, purged hardcoded hex colors, AppIconButton/FormSection/EmptyState components |
| **Typography** | Shared lib/typography.ts, added shorthand aliases (h1-h6, body1-3, subtitle, button1-2) |
| **Dead code removal** | 32 unused files deleted, 60 unused exports removed, 10 unused npm deps uninstalled |
| **TypeScript** | Fixed all 248 pre-existing errors → 0 errors |
| **Reminders decision** | Flagged for removal — zero user engagement |
| **PRs** | #133 (refactoring → james-develop), #134 (james-develop → main) |

### Landing Page (petiogo.com)

| Task | Detail |
|------|--------|
| **AI-first positioning** | Updated H1, hero subtitle, feature cards (Reminders → AI Assistant), pricing tiers, testimonials, footer |
| **Blog system** | MDX engine with tag filters, load-more pagination, featured hero post, sticky TOC, related posts, reading progress bar |
| **5 quality articles** | Can My Dog Eat That, Dog Food Allergies, Puppy First Week, Pet Food Recalls, AI Pet Care 2026 — all 2000-2500 words, cited sources, personal voice, visual components (Callout/QuickAnswer/StatCard) |
| **SEO audit + fixes** | robots.txt, dynamic sitemap.ts, FAQPage schema (5 Q&A), Organization schema, BlogPosting schema, OG tags on all pages, canonical URLs, fixed 11 broken footer links, fixed About canonical bug |
| **AI search optimization** | llms.txt deployed with correct domain + all pages |
| **Analytics** | Google Analytics (G-NX2Y1CWL97) + Microsoft Clarity installed |
| **Performance** | Removed filter:blur animations (text glitch cause), restored Lenis smooth scroll, enabled remark-gfm for table rendering |

### Startup-OS Context

| Task | Detail |
|------|--------|
| **product.md** | Features restructured (AI-First/Pet Life/Infrastructure), tech stack added, completed work logged, roadmap added |
| **company.md** | Founded 2025, 3 co-founders + equity split, $470 total spend, vision + values filled, stage updated to "Live on iOS" |
| **customers.md** | Reminders reference removed |
| **market.md** | Memories as competitive differentiator added |
| **metrics.md** | North Star defined (weekly AI chat sessions), AARRR framework + targets, guardrail metrics, OKRs with completion status |

---

## What's Next — Prioritized Roadmap

### Immediate — COMPLETED (Apr 7)

| # | Action | Owner | Status |
|---|--------|-------|--------|
| 1 | Submit sitemap to Google Search Console | James | Done — 11 URLs submitted, crawling started |
| 2 | Submit to Bing Webmaster Tools | James | Done — imported from GSC |
| 3 | Remove reminders tab + routes from mobile app | James | Done |
| 4 | Update App Store screenshots + description | Ngoc + James | Done |

### Short-Term (This Month)

#### Global / US Market (continued)
| # | Action | Owner | Effort | Status |
|---|--------|-------|--------|--------|
| 5 | ~~Write "Can My Cat Eat That?" companion post~~ | James | 2 hrs | **Done** — covered by Vietnamese "mèo ăn được gì" post + EN blog already has similar content |
| 6 | ~~Build /tools/food-checker interactive page~~ | James | 1 day | **Done** — 64 foods, bilingual, search, dog/cat tabs, linked in footer |
| 7 | Customer interviews (Mom Test) | James | Ongoing | 0 post-pivot validation — all customer insights are hypothesized |
| 8 | Product Hunt launch | James | 1 day | Backlinks + discovery + early adopter acquisition |
| 9 | Google Play listing | James | 1 day | Android users can't install yet |

#### Vietnam Market Expansion
| # | Action | Owner | Effort | Status |
|---|--------|-------|--------|--------|
| 10 | ~~Vietnam competitor research~~ | James | Half day | **Done** — PawHub mapped: 447 listings, 36 blog posts, AI Doctor (Beta), 5-person team |
| 11 | ~~Landing page i18n (next-intl)~~ | James | 2-3 hrs | **Done** — [locale] routing, EN/VI, language switcher |
| 12 | ~~Extract strings → en.json + vi.json~~ | James | 3-4 hrs | **Done** — all pages translated |
| 13 | ~~Vietnamese SEO metadata~~ | James | 1-2 hrs | **Done** — hreflang, OG, locale-aware generateMetadata |
| 14 | ~~Language switcher in navbar~~ | James | 30 min | **Done** — dropdown with ARIA, preserves path |
| 15 | ~~Vietnamese blog content (first 3 posts)~~ | James | 3 days | **Done** — 3 posts: chó ăn được gì, mèo ăn được gì, dị ứng thức ăn chó. Scanner CTAs, VN brands, 2000+ words each |
| 16 | ~~Build /vi/tools/kiem-tra-thuc-an (food checker)~~ | James | 1 day | **Done** — 64 foods, bilingual, search, dog/cat tabs, VN-specific foods. Linked in footer |
| 17 | ~~Blog locale filtering~~ | James | 1 hr | **Done** — EN users see only EN posts, VI users see only VI posts |
| 18 | Vietnamese App Store listing | James | 1 day | Title, description, screenshots in Vietnamese |
| 19 | VN pricing tier (49-99K VND/month) | James | Half day | $35/yr doesn't match Vietnamese purchasing power |

### Medium-Term (This Quarter)

#### Global / US Market
| # | Action | Owner | Effort | Why |
|---|--------|-------|--------|-----|
| 17 | Set up analytics events | James | Half day | Track activation (profile + first chat), scanner usage, memory creation |
| 18 | Measure North Star | James | 1 hr/week | Weekly AI chat sessions per active user — habit indicator |
| 19 | A/B test onboarding flow | James | 1 week | Current survey → paywall needs validation |
| 20 | 5 more blog posts (EN) | James | 1 week | Puppy feeding, vet frequency, pet insurance, cat behavior, breed guides |
| 21 | ASO (App Store Optimization) | James | 2 days | Keywords, screenshots, description for AI pet care queries |
| 22 | Submit to pet app directories | James | 1 day | AlternativeTo, G2, pet-specific directories for backlinks |

#### Vietnam Market
| # | Action | Owner | Effort | Why |
|---|--------|-------|--------|-----|
| 23 | Vietnamese blog posts #4-10 (VN brand comparisons, label reading, cost, vaccination, cheap food) | James | 2 weeks | Fill gaps PawHub doesn't cover — scanner angle on every post |
| 24 | TikTok scanner demos (Vietnamese) | James | Ongoing | "Boss đang ăn gì?" — scan popular VN pet food brands, short-form video |
| 25 | Zalo OA setup + community seeding | James | 2 days | Vietnamese pet parents live on Zalo and Facebook |
| 26 | Facebook group strategy (VN pet communities) | James | Ongoing | Seed presence in HCMC/Hanoi breed-specific and city-specific groups |
| 27 | VN-specific ASO | James | 1 day | Vietnamese keywords in App Store / Play Store |

---

## Key Decisions Made

1. **Reminders removed** — zero user engagement despite being a core v1 tab
2. **AI-first positioning** — all messaging pivoted from "organized" to "AI that knows your pet"
3. **Blog quality over quantity** — deleted 3 thin posts, rewrote 5 with cited sources + personal voice
4. **Typography shorthand aliases kept** — h1-h6, body1-3 are intended (not renamed to long-form)
5. **Lenis smooth scroll kept** — but LensFocusEffect (backdrop-blur overlay) permanently removed
6. **Vietnam market expansion (Apr 7)** — dual-market strategy: global/US (primary, PMF focus) + Vietnam (home market, organic expansion). Same product, same vision, no feature fragmentation. Vietnam gets: localized landing page, Vietnamese SEO content, local community (Zalo/Facebook), adjusted pricing. App already supports Vietnamese language.

---

## Blockers / Risks

| Risk | Impact | Mitigation |
|------|--------|-----------|
| 0 customer interviews post-pivot | HIGH — all personas and JTBD are hypothesized | Vy to start Mom Test interviews this month |
| Google Play not live | MEDIUM — losing Android users | Ship this month |
| No analytics events | MEDIUM — can't measure activation or retention | Set up this month |
| Dual-market split focus | MEDIUM — risk of doing neither market well | Vietnam is GTM/content only, no product fragmentation. James handles landing page i18n, Vy handles VN content/community |
