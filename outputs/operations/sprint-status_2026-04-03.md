# Petio Sprint Status — 2026-04-03

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

### Immediate (This Week)

| # | Action | Owner | Effort | Why |
|---|--------|-------|--------|-----|
| 1 | Submit sitemap to Google Search Console | James | 10 min | Unblocks indexing — nothing ranks until Google knows we exist |
| 2 | Submit to Bing Webmaster Tools | James | 10 min | Powers Copilot + ChatGPT browse — AI search traffic |
| 3 | Remove reminders tab + routes from mobile app | James | 2-3 hrs | Dead feature adding complexity and confusing new users |
| 4 | Update App Store screenshots + description | Ngoc + James | 1 day | Currently reflects old "organized" positioning, not AI-first |

### Short-Term (This Month)

| # | Action | Owner | Effort | Why |
|---|--------|-------|--------|-----|
| 5 | Write "Can My Cat Eat That?" companion post | Vy + James | 2 hrs | Mirrors high-performing dog post for untapped cat keyword volume |
| 6 | Build /tools/food-checker interactive page | James | 1 day | Highly linkable free tool, natural product demo for scanner |
| 7 | Customer interviews (Mom Test) | Vy | Ongoing | 0 post-pivot validation — all customer insights are hypothesized |
| 8 | Product Hunt launch | Vy | 1 day | Backlinks + discovery + early adopter acquisition |
| 9 | Google Play listing | James | 1 day | Android users can't install yet |

### Medium-Term (This Quarter)

| # | Action | Owner | Effort | Why |
|---|--------|-------|--------|-----|
| 10 | Set up analytics events | James | Half day | Track activation (profile + first chat), scanner usage, memory creation |
| 11 | Measure North Star | James | 1 hr/week | Weekly AI chat sessions per active user — habit indicator |
| 12 | A/B test onboarding flow | James + Vy | 1 week | Current survey → paywall needs validation |
| 13 | 5 more blog posts | Vy + James | 1 week | Puppy feeding, vet frequency, pet insurance, cat behavior, breed guides |
| 14 | ASO (App Store Optimization) | Ngoc + James | 2 days | Keywords, screenshots, description for AI pet care queries |
| 15 | Submit to pet app directories | Vy | 1 day | AlternativeTo, G2, pet-specific directories for backlinks |

---

## Key Decisions Made

1. **Reminders removed** — zero user engagement despite being a core v1 tab
2. **AI-first positioning** — all messaging pivoted from "organized" to "AI that knows your pet"
3. **Blog quality over quantity** — deleted 3 thin posts, rewrote 5 with cited sources + personal voice
4. **Typography shorthand aliases kept** — h1-h6, body1-3 are intended (not renamed to long-form)
5. **Lenis smooth scroll kept** — but LensFocusEffect (backdrop-blur overlay) permanently removed

---

## Blockers / Risks

| Risk | Impact | Mitigation |
|------|--------|-----------|
| 0 customer interviews post-pivot | HIGH — all personas and JTBD are hypothesized | Vy to start Mom Test interviews this month |
| Google Play not live | MEDIUM — losing Android users | Ship this month |
| No analytics events | MEDIUM — can't measure activation or retention | Set up this month |
| App Store screenshots outdated | MEDIUM — first impression doesn't match AI positioning | Update with Ngoc this week |
