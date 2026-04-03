# Product Context

## Product Overview
- **Product Name**: Petio
- **Category**: AI-first pet care & wellness
- **Platform**: Mobile (iOS & Android)
- **Tech Stack**: React Native / Expo, Supabase
- **Website**: https://petiogo.com (pre-pivot — website reflects old positioning)

## Problem & Solution
- **Core Problem**: Pet parents lack personalized, contextual guidance for their pet's behavior, wellness, and safety — they rely on generic Google searches, guesswork, and expensive vet visits for everyday questions.
- **Current Alternatives**: Google search, vet visits ($50-150 per consultation), pet forums/Reddit, generic pet care apps (health tracking only), pet food label reading (manual, error-prone)
- **Our Solution**: AI-first pet care app that knows your pet personally and provides contextual behavior guidance, wellness insights, and product safety scanning.
- **Key Differentiator**: AI that has full context of each pet (breed, age, health history, allergies, conditions) — not generic advice, but personalized intelligence.

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
