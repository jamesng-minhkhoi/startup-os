# Product Context

## Product Overview
- **Product Name**: Petio
- **Category**: AI-first pet care & wellness
- **Platform**: Mobile (iOS & Android)
- **Tech Stack**: React Native / Expo, Supabase
- **Website**: https://petiogo.com (updated — reflects AI-first positioning)

## Problem & Solution
- **Core Problem**: Pet parents lack personalized, contextual guidance for their pet's behavior, wellness, and safety — they rely on generic Google searches, guesswork, and expensive vet visits for everyday questions.
- **Current Alternatives**: Google search, vet visits ($50-150 per consultation), pet forums/Reddit, generic pet care apps (health tracking only), pet food label reading (manual, error-prone)
- **Our Solution**: AI-first pet care app that knows your pet personally and provides contextual behavior guidance, wellness insights, and product safety scanning.
- **Key Differentiator**: AI that has full context of each pet (breed, age, health history, allergies, conditions) — not generic advice, but personalized intelligence.

### 5 Core Differentiators (Value Proposition Framework — 2026-04-06)
1. **AI-native system (not feature-based AI)**: AI is the core of the experience, not an add-on — every interaction is AI-powered
2. **Scan-first interaction model**: Users scan food, documents → auto insights & actions with minimal effort
3. **Agentic behavior (action-driven AI)**: AI doesn't just answer — it updates pet data, suggests actions, triggers reminders
4. **Contextual intelligence**: App understands pet profile, user habits, and current screen/context for relevant suggestions
5. **Emotional + functional integration**: Combines utility (tracking, health) with emotion (memories, bonding) — not one or the other

## Core Features (Post-Pivot)

### AI-First (New — Differentiators)
1. **AI Chat (Personalized)**: Gemini-powered chatbot with full context of user's pets — breed, age, weight, health history, allergies, conditions. Uses function calling for rich widget responses (health charts, product reports). Not generic advice — personalized intelligence.
2. **Product Scanner**: Scan pet food/treat/product barcodes to detect allergens and unsafe ingredients specific to the user's pet. Integrated into AI chat as a tool.

### Pet Life (Core Experience)
3. **Pet Profiles**: Multi-step creation wizard (species, breed, age, health, personality traits, habits). Supports dogs, cats, and other species. Photo upload, weight tracking, vaccination/allergy/medication/diet records.
4. **Memories**: Photo journal with calendar view — capture and browse pet moments by date. Social features (comments, reactions) for family engagement. Emerging as a key retention feature.
5. **Statistics**: Per-pet health dashboard — weight trends, BMI/BCS, nutrition, activity metrics with visual charts.
6. **Document Storage**: Pet passports, vet invoices, IDs with tagging to specific pets.

### Infrastructure
7. **Family Sync**: Multi-member families, pet sharing, invitation system.
8. **Onboarding**: Survey-based onboarding (pet types, count, feature interests) feeding into social proof paywall.
9. **Notifications**: Push notification system for engagement.

### Removed Features
- **Smart Reminders**: Removed — zero real user engagement despite being a core v1 tab. Users don't adopt reminder workflows for pet care.

## Tech Stack (Actual)
- **Framework**: React Native / Expo SDK 55
- **Backend**: Supabase (auth, Postgres, storage, realtime)
- **AI**: Google Gemini API with function calling (tool registry pattern)
- **Payments**: RevenueCat (freemium → Plus subscription)
- **State**: Zustand (14 slices, persisted to AsyncStorage)
- **Navigation**: Expo Router (file-based routing)
- **UI**: Custom design system with token-based primitives (no Tailwind/NativeWind)

## Positioning (Post-Pivot)
- **Market Category**: AI pet care assistant
- **Target Customer**: Pet parents who want personalized, intelligent pet care guidance
- **Positioning Statement**: "For pet parents who want more than generic advice, Petio is the AI pet care assistant that knows your pet personally — providing behavior guidance, wellness insights, and product safety scanning tailored to your pet's unique profile."
- **Brand Statement** (from Value Prop): PETIO is not just a tool — it acts as a companion that helps users care smarter and connect deeper with their pets

### Design Principles (Value Proposition Framework)
- **AI-first experience**: AI is embedded across the app to assist, automate, and personalize
- **Low-effort interaction**: Minimal manual input, fast actions
- **Context-aware intelligence**: Suggestions based on pet data & behavior
- **Daily usability**: Designed to be opened and used every day, not occasionally

## Hypothesized User Segments
1. **First-Time Owner**: New to pet ownership, high anxiety, lots of questions, needs guidance on everything (feeding, behavior, training, vet schedules). High willingness to trust an AI assistant.
2. **Busy Owner**: Experienced but time-constrained. Wants quick answers, product safety checks, and family sync without deep research. Values convenience and speed.
3. **Superuser**: Experienced, detail-oriented. Tracks everything, wants deep health analytics, reads ingredient labels, compares products. Values depth and data.

## What We're NOT Building
- Not a vet telemedicine platform (we guide, not diagnose)
- Not a pet social network
- Not a hardware/wearable product
- Not a marketplace/e-commerce

## Business Model
- **Revenue Model**: Freemium with subscription upgrade
- **Pricing (Dual Market)**:
  - Free: 3 scans/day, 5 AI messages/day, 1 pet profile
  - Plus (US/Global): $5.99/mo or $47.99/yr — unlimited scans, AI chat, 5 pet profiles, allergen watchlist, family sharing
  - Plus (Vietnam): 79K VND/mo or 599K VND/yr — same features, localized pricing
- **Launch**: June 14, 2026 (relaunch — AI-first pivot, first Product Hunt)
- **Unit Economics**: <!-- To be measured -->

## Website & Content (petiogo.com)
- **Stack**: Next.js 16, Tailwind v4, Framer Motion, Radix, Lenis smooth scroll, next-intl (i18n)
- **i18n**: Bilingual EN/VI with [locale] routing, language switcher dropdown, locale-aware metadata/SEO, hreflang alternates
- **SEO**: Sitemap, robots.txt, JSON-LD (SoftwareApplication, Organization, FAQPage, BlogPosting), Open Graph, canonical URLs, llms.txt for AI search
- **Analytics**: Google Analytics (G-NX2Y1CWL97), Microsoft Clarity
- **Blog**: 8 articles total (5 EN, 3 VI) with MDX, locale-aware filtering, tag filtering, pagination, TOC, related posts
- **English content**: Dog food safety, food allergies, puppy guides, pet food recalls, AI pet care thought leadership
- **Vietnamese content**: Chó ăn được gì (A-Z), mèo ăn được gì, dị ứng thức ăn chó — all with scanner CTAs, VN food brands, 2000+ words
- **Food Checker Tool**: /tools/food-checker — 64 foods with dog/cat safety status, search, bilingual, linked in footer. Free web tool for SEO traffic

## What's Been Completed (as of 2026-04-03)

### Mobile App (petio-mobile)
- App live on iOS App Store
- Major codebase refactoring: split 5 mega-files, consolidated duplication, removed 32 dead files
- Design system improvements: shadow/size tokens, StyleProps, centralized haptics/motion
- 0 TypeScript errors (fixed 248 pre-existing)
- 10 unused npm dependencies removed
- Reminders feature removed (zero engagement)
- PR #133 (refactoring) and PR #134 (james-develop → main) created

### Landing Page (petio-landingpage)
- H1 and messaging updated to AI-first positioning
- Feature cards updated: "Smart Reminders" → "AI Assistant"
- Blog system: MDX with Callout/QuickAnswer/StatCard components, tag filters, load-more pagination, sticky TOC, related posts, reading progress bar
- 5 quality English blog posts (2000-2500 words each, cited sources, personal voice)
- SEO: robots.txt, dynamic sitemap, FAQPage schema, Organization schema, BlogPosting schema, OG tags on all pages, llms.txt
- Google Analytics + Microsoft Clarity installed
- Scroll performance fixed (removed backdrop-blur glitch)
- All broken footer links fixed

### Landing Page i18n + Vietnam Content (Apr 7)
- Full i18n with next-intl: [locale] routing, middleware, EN/VI message files
- All pages translated: Home, Features, Pricing, About, Blog, FAQ, CTA, Navbar, Footer
- Language switcher dropdown with ARIA accessibility, preserves current path
- Locale-aware metadata (generateMetadata) on all pages with hreflang alternates
- Blog locale filtering: EN users see EN posts only, VI users see VI posts only
- 3 Vietnamese blog posts: chó ăn được gì, mèo ăn được gì, dị ứng thức ăn chó (scanner CTAs, VN brands)
- Food Checker tool at /tools/food-checker: 64 foods, bilingual, search, dog/cat tabs, VN-specific foods, linked in footer
- FAQ JSON-LD reads from translations (Vietnamese users get Vietnamese structured data)

## What's Next (Prioritized — updated Apr 7)

### Completed (Apr 7)
- GSC sitemap submitted, Bing Webmaster imported
- Reminders removed, App Store screenshots updated
- Vietnam competitor research (PawHub fully mapped)
- Landing page i18n (EN/VI, all pages, language switcher)
- 3 Vietnamese blog posts with scanner angle
- Food Checker tool (64 foods, bilingual)
- Blog locale filtering (EN/VI separated)

### Blockers (Before Marketing)
1. **Google Play listing (Vietnamese)** — 70%+ of VN market is Android
2. **Vietnamese App Store listing** — title, description, screenshots in Vietnamese
3. **VN pricing tier (79K VND/mo)** — must be set before any VN marketing
4. **Analytics events** — track activation, scanner usage, chat, paywall, conversions
5. **Referral tracking (UTM links)** — can't attribute installs to channels without this

### Pre-Launch (Apr–Jun 2026)
6. **Content engine** — 10 EN blog posts, 10 VI blog posts, TikTok on both markets (4-5/week)
7. **Community seeding** — Reddit (US), Facebook pet groups (VN), Facebook allergy groups (US)
8. **Customer interviews (Mom Test)** — 0 post-pivot validation done
9. **Micro-influencer outreach** — US (free Plus for review), VN (~$150/post KOL)
10. **Product Hunt ship page** — 2 weeks before launch

### Launch (June 14, 2026)
11. **Product Hunt + TikTok blitz + all channels** — both markets simultaneously
12. **Giveaway campaigns (VN)** — comment + share → win Petio Plus

### Post-Launch (This Quarter)
13. **Measure North Star** — weekly AI chat sessions per active user
14. **A/B test onboarding** — current survey → paywall needs validation
15. **ASO** — keywords, screenshots, description for AI pet care queries (EN + VI)
16. **Zalo OA + Facebook group strategy** — Vietnamese community channels
17. **Referral program** — "Give 1 month, get 1 month" (activate after proving retention)
18. **Distribution partnerships (VN)** — pending Vy's decision on rev share model
