# Product Context

## Product Overview
- **Product Name**: VocabX (multi-app platform: VocabX, MedVocab, IELTS Vocab, Lexicon, LegalLex)
- **Category**: Education / Vocabulary Learning
- **Platform**: Mobile (iOS primary, Android planned)
- **Tech Stack**: React Native (Expo SDK 55), Supabase, Zustand, ts-fsrs (FSRS algorithm), RevenueCat, PostHog

## Problem & Solution
- **Core Problem**: Vocabulary learning apps are either powerful but ugly/complex (Anki) or beautiful but shallow (Duolingo, Drops). No app combines serious spaced repetition with modern mobile UX for specific professional niches.
- **Current Alternatives**: Duolingo ($12.99/mo), Anki (free/$24.99), Quizlet ($7.99/mo), Memrise ($9/mo), WordUp ($4.99/mo), Vocabulary.com, Drops ($13/mo), Brainscape ($19.99/mo)
- **Our Solution**: FSRS-powered vocabulary learning with TikTok-style discovery feed, niche-specific content (medical, IELTS, legal, literary, general)
- **Key Differentiator**: Anki's brain (FSRS) + TikTok's UX + niche specialization

## Positioning (Updated 2026-04-02)
- **Market Category**: Niche Vocabulary Learning Apps (sub-category creation -- avoids fighting Duolingo on "language learning")
- **Target Customer**: IELTS test-takers (beachhead), then med students, law students, young professionals, literary word lovers
- **Positioning Statement**: "For motivated learners in specific fields, VocabX is the niche vocabulary platform that combines a scientifically superior spaced repetition algorithm with a premium, mobile-native experience."
- **Beachhead App**: IELTS Vocab (launched first -- 4.1M annual test-takers, exam deadline urgency, high willingness to pay, massive ASO opportunity)
- **Full positioning & GTM**: See `outputs/strategy/positioning_vocabx_2026-04-02.md`

## Features & Roadmap
- **Core Features**: TikTok-style word feed, FSRS review, quiz games (MC, FITB, Match), word detail (definitions, examples, etymology, audio), streaks, progress dashboard, 13 achievements, iOS widget, push notifications, offline cache, free-tier gating
- **Current Focus**: IELTS Vocab launch (beachhead niche). Multi-app strategy confirmed -- launch sequence: IELTS Vocab -> MedVocab + VocabX General -> LegalLex + Lexicon
- **What We're NOT Building**: User-generated content, full language courses, AI chat features (yet)

## Business Model
- **Revenue Model**: Freemium + Subscription (RevenueCat)
- **Pricing**: IELTS Vocab $7.99/mo ($49.99/yr); VocabX $7.99/mo ($49.99/yr); MedVocab $14.99/mo ($99.99/yr); LegalLex $12.99/mo ($89.99/yr); Lexicon $5.99/mo ($39.99/yr)
- **Unit Economics**: Not yet measured (pre-launch)
- **Free Tier Limits**: 5 words/day, 5 reviews/day, 1 quiz/day, 10 bookmarks, no audio/AI
