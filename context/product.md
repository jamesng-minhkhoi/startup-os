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
- **Pricing**:
  - Free: 1 pet, 1 family, 5 documents, limited AI chat, 3 memories/day
  - Plus: $2.92/mo ($34.99/year) — unlimited pets, families, documents, AI chat, product scanner, advanced insights
- **Unit Economics**: <!-- To be measured -->

## Website & Content (petiogo.com)
- **Stack**: Next.js 16, Tailwind v4, Framer Motion, Radix, Lenis smooth scroll
- **SEO**: Sitemap, robots.txt, JSON-LD (SoftwareApplication, Organization, FAQPage, BlogPosting), Open Graph, canonical URLs, llms.txt for AI search
- **Analytics**: Google Analytics (G-NX2Y1CWL97), Microsoft Clarity
- **Blog**: 5 SEO-researched articles with MDX, tag filtering, pagination, TOC, related posts
- **Content topics**: Dog food safety, food allergies, puppy guides, pet food recalls, AI pet care thought leadership

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
- 5 quality blog posts (2000-2500 words each, cited sources, personal voice)
- SEO: robots.txt, dynamic sitemap, FAQPage schema, Organization schema, BlogPosting schema, OG tags on all pages, llms.txt
- Google Analytics + Microsoft Clarity installed
- Scroll performance fixed (removed backdrop-blur glitch)
- All broken footer links fixed

## What's Next (Prioritized)

### Immediate (This Week)
1. **Submit sitemap to Google Search Console** — manual step, critical for indexing
2. **Submit to Bing Webmaster Tools** — powers Copilot + ChatGPT browse
3. **Remove reminders from mobile app** — code still exists, tab still shows, need to remove the tab + routes
4. **App Store screenshots/description update** — reflect AI-first positioning, not "organized"

### Short-Term (This Month)
5. **Write "Can My Cat Eat That?" blog post** — mirror dog food post for cat audience (untapped keyword volume)
6. **Build interactive food safety checker** — free tool at /tools/food-checker, highly linkable
7. **Customer interviews** — 0 post-pivot validation done (customers.md notes this)
8. **Product Hunt launch** — backlinks + discovery
9. **Google Play listing** — app not yet on Play Store

### Medium-Term (This Quarter)
10. **Measure North Star metric** — weekly AI chat sessions per active user
11. **Set up analytics events** — track activation (profile + first chat), scanner usage, memory creation
12. **A/B test onboarding** — current survey → paywall flow needs validation
13. **Content: 5 more blog posts** targeting high-volume queries (puppy feeding, vet visit frequency, pet insurance, cat behavior)
14. **ASO (App Store Optimization)** — keywords, screenshots, description for AI pet care queries
