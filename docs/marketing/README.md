# Petio Marketing Ops

The system for producing, tracking, and learning from marketing content across both markets (VN + Global).

## Folder map

```
docs/marketing/
├── README.md                  ← you are here
├── content/
│   ├── content-tracker.md     ← master log: every piece of content + its performance
│   └── calendars/             ← dated posting calendars (the plan)
│       ├── content-calendar_vn_2026-06-22.md
│       └── global-seeding_2026-06-22.md
├── experiments/
│   └── ab-test-log.md         ← every A/B test: hypothesis, variants, result, decision
├── templates/                 ← AI prompts to generate on-brand content fast
│   ├── README.md
│   ├── tiktok-scan-demo.md
│   ├── fb-group-value-post.md
│   ├── ig-carousel.md
│   ├── threads-vn-generator-prompt.md   ← community-adaptive Threads generator
│   ├── threads-vn-pet-style-guide.md    ← Threads VN voice reference
│   ├── reddit-helpful-comment.md
│   ├── blog-post-seo.md
│   └── ab-test-brief.md
├── messaging-guardrails.md    ← canonical "what Petio is/isn't" + voice-by-channel
└── *-plan.md                  ← strategy docs (us-launch, vietnam-growth, vn-launch)
```

## The loop (how it all connects)

```
calendars/  →  templates/  →  content-tracker.md  →  experiments/ab-test-log.md
  (plan)       (generate)        (track + measure)        (learn → adjust calendar)
```

1. **Plan** — calendars say what to post, when, on which channel.
2. **Generate** — use a `templates/` prompt in Claude to draft the actual copy/script on-brand.
3. **Track** — log every published piece in `content-tracker.md` with its metrics.
4. **Test & learn** — when you want to compare two approaches, write an `ab-test-brief`, run it, record the result in `ab-test-log.md`, feed the winner back into the calendar.

## Rules baked into every template
- **Read `context/product.md` + `context/customers.md` first** so output is on-brand and personalized.
- **Value-first, app-second** during the iOS-only window (see launch-state).
- **Native Vietnamese** for VN — never translated from English.
- **Hero CTA = free Food Checker** (`petiogo.com/vi/tools/kiem-tra-thuc-an`) while Play Store is pending.
- **No medical/diagnosis claims.** "Kiểm tra thành phần", not "chẩn đoán".
