# Petio Growth Funnel & Strategy Map

**Launch:** June 14, 2026 | **Markets:** US (primary) + Vietnam (50/50 split)

---

## The Funnel

```mermaid
flowchart TD
    subgraph ACQ["ACQUISITION — How they find us"]
        direction LR
        SEO["SEO Blog + Food Checker\n(both markets)"]
        TK_US["TikTok US\n'Is This Safe?'"]
        TK_VN["TikTok VN\n'Boss đang ăn gì?'"]
        RD["Reddit\nr/dogs, r/dogallergies"]
        FB_US["Facebook\nAllergy groups (US)"]
        FB_VN["Facebook\nPet groups (VN)"]
        ASO["ASO\nApp Store + Play Store"]
        PH["Product Hunt\nJune 14"]
        KOL_US["Micro-influencers (US)\nFree Plus for review"]
        KOL_VN["Micro-KOL (VN)\n~$150/post"]
        PARTNER["Distribution Partners (VN)\n20-30% rev share"]
        ZALO["Zalo OA (VN)"]
    end

    subgraph ACT["ACTIVATION — First value moment"]
        DOWNLOAD["Download App"]
        PROFILE["Create Pet Profile\n(name, breed, allergies)"]
        SCAN1["First Scan\n⚡ under 30 seconds"]
        CHAT1["First AI Chat\n'Is this normal?'"]
    end

    subgraph RET["RETENTION — They come back"]
        HABIT["Scan Habit\n3+ scans/week"]
        AICHAT["AI Chat Habit\n3+ sessions/week ⭐ North Star"]
        MEMORY["Save Memories\nPhotos, milestones"]
        HEALTH["Health Tracking\nSymptoms, vet visits"]
    end

    subgraph REV["REVENUE — They pay"]
        WALL["Hit Paywall\n4th scan or 6th AI message"]
        TRIAL["7-Day Free Trial"]
        PAID["Petio Plus\nUS: $5.99/mo | VN: 79K VND/mo"]
    end

    subgraph REF["REFERRAL — They bring others"]
        SHARE["Share Scan Result\nBranded card + App Store link"]
        FAMILY["Family Sync\nInvite partner/sitter"]
        REFER["Referral Program\n'Give 1 month, get 1 month'"]
    end

    ACQ --> DOWNLOAD
    DOWNLOAD --> PROFILE
    PROFILE --> SCAN1
    PROFILE --> CHAT1
    SCAN1 --> HABIT
    CHAT1 --> AICHAT
    HABIT --> WALL
    AICHAT --> WALL
    SCAN1 --> MEMORY
    CHAT1 --> HEALTH
    WALL --> TRIAL
    TRIAL --> PAID
    HABIT --> SHARE
    PAID --> FAMILY
    PAID --> REFER
    SHARE -->|"new user"| DOWNLOAD
    FAMILY -->|"new user"| DOWNLOAD
    REFER -->|"new user"| DOWNLOAD
```

---

## Channel Strategy by Market

```mermaid
flowchart LR
    subgraph US["🇺🇸 US / Global"]
        direction TB
        US1["SEO Blog\n10 posts, food checker tool\n$0 — compounding"]
        US2["TikTok 'Is This Safe?'\n4-5/week, boost winners\n$100-250/mo"]
        US3["Reddit Seeding\nr/dogs, r/dogallergies\n$0 — 30min/day"]
        US4["Facebook Allergy Groups\n$0 — 15min/day"]
        US5["ASO\n$0 — optimize monthly"]
        US6["Product Hunt\nJune 14\n$0"]
        US7["Micro-Influencers\n5-10 creators\n$0 cash (free Plus)"]
    end

    subgraph VN["🇻🇳 Vietnam"]
        direction TB
        VN1["Facebook Pet Groups\n10 groups, daily presence\n$0 — #1 channel in VN"]
        VN2["TikTok 'Boss đang ăn gì?'\n5/week, boost winners\n$100-250/mo"]
        VN3["Vietnamese SEO Blog\n10 posts, scanner CTAs\n$0 — out-content PawHub"]
        VN4["Zalo OA\nCustomer support + retention\n$0"]
        VN5["Micro-KOL\n5-10 pet TikTokers\n~$150/post"]
        VN6["Distribution Partners\nRev share 20-30%\nPending Vy's decision"]
        VN7["Giveaways\nMonthly, in FB groups\n$50-100/campaign"]
    end

    US1 & US2 & US3 & US4 & US5 & US6 & US7 --> INST_US["Installs"]
    VN1 & VN2 & VN3 & VN4 & VN5 & VN6 & VN7 --> INST_VN["Installs"]
```

---

## Growth Loops

```mermaid
flowchart LR
    A["User scans product"] --> B["Gets result:\nSAFE / UNSAFE"]
    B --> C["Shares branded\nresult card"]
    C --> D["Friend sees card\n+ App Store link"]
    D --> E["Friend downloads"]
    E --> A

    F["User upgrades\nto Plus"] --> G["Invites family\nvia Family Sync"]
    G --> H["Family member\ndownloads app"]
    H --> I["Gets value from\nshared pet profile"]
    I --> J["Hits own paywall\nafter 7 days"]
    J --> F

    K["Happy user\nDay 14+"] --> L["Push notification:\n'Give 1 month free'"]
    L --> M["Shares referral\nlink"]
    M --> N["New user gets\n1 month free"]
    N --> K
```

---

## Funnel Metrics & Targets

```mermaid
flowchart TD
    A["ACQUISITION\n3,000+ installs by Launch +30"] --> B["ACTIVATION\nProfile + first scan in 90s\nTarget: 60% of downloads"]
    B --> C["RETENTION\n3+ AI chats/week ⭐\nD7: >25% | D30: >15%"]
    C --> D["REVENUE\n>5% free-to-paid\nUS: $5.99/mo | VN: 79K VND/mo"]
    D --> E["REFERRAL\n10% share rate on scans\n20% of Plus invite family"]
```

| Stage | Metric | GO | ITERATE | KILL |
|-------|--------|-----|---------|------|
| **Acquisition** | Total installs (Launch +30) | >3,000 | 1,000-3,000 | <1,000 |
| **Activation** | Profile + first scan completion | >60% | 40-60% | <40% |
| **Retention** | D30 retention | >15% | 8-15% | <8% |
| **Revenue** | Free-to-paid conversion | >5% | 2-5% | <2% |
| **Revenue** | Paying users (Launch +30) | >150 | 50-150 | <50 |
| **Referral** | Scan result share rate | >10% | 5-10% | <5% |

### Vietnam-Specific (Launch +90)

| Metric | WIN | COMPETITIVE | LOSING |
|--------|-----|-------------|--------|
| Vietnam installs | >10,000 | 3,000-10,000 | <3,000 |
| TikTok VN followers | >5,000 | 1,000-5,000 | <1,000 |
| Vietnamese blog rankings ("chó ăn được gì") | Top 3 | Page 1 | Not ranking |

---

## Timeline to Launch

```mermaid
gantt
    title Petio Launch Timeline
    dateFormat YYYY-MM-DD
    axisFormat %b %d

    section Blockers
    Play Store listing (VI)           :crit, b1, 2026-04-08, 2d
    VN App Store listing              :crit, b2, 2026-04-08, 2d
    VN pricing in RevenueCat          :b3, 2026-04-08, 1d
    Analytics events                  :crit, b4, 2026-04-10, 2d
    Referral tracking (UTM)           :b5, 2026-04-14, 2d

    section Content Engine
    EN blog posts #6-10               :c1, 2026-04-21, 28d
    VI blog posts #4-10               :c2, 2026-04-21, 28d
    TikTok US (4-5/week)              :c3, 2026-04-21, 54d
    TikTok VN (5/week)                :c4, 2026-04-21, 54d

    section Community
    Reddit warm-up (30+ days)         :cm1, 2026-04-14, 35d
    FB groups VN (observe → seed)     :cm2, 2026-04-14, 60d
    FB allergy groups US              :cm3, 2026-05-05, 40d
    Zalo OA setup                     :cm4, 2026-04-21, 3d

    section Pre-Launch
    Product Hunt ship page            :p1, 2026-05-31, 14d
    US micro-influencer outreach      :p2, 2026-05-19, 14d
    VN micro-KOL outreach             :p3, 2026-05-19, 14d
    Partner onboarding (if approved)  :p4, 2026-05-19, 14d

    section Launch
    🚀 LAUNCH DAY                    :milestone, crit, 2026-06-14, 0d
    Launch week blitz                 :l1, 2026-06-14, 7d
    Post-launch scale                 :l2, 2026-06-21, 85d

    section Checkpoints
    Week 4 health check               :milestone, 2026-05-05, 0d
    Launch +7 metrics                  :milestone, 2026-06-21, 0d
    Launch +30 GO/ITERATE/KILL         :milestone, 2026-07-14, 0d
    VN 90-day (10K target)             :milestone, 2026-09-14, 0d
```

---

## Ownership

```mermaid
flowchart TD
    subgraph JAMES["James — Eng + Strategy"]
        J1["Play Store + App Store listings"]
        J2["Analytics + referral tracking"]
        J3["Blog posts (EN + VI)"]
        J4["TikTok filming (EN + VI)"]
        J5["Reddit + FB allergy groups (US)"]
        J6["Product Hunt"]
        J7["US micro-influencer outreach"]
        J8["Pricing + paywall"]
    end

    subgraph VY["Vy — Product + Marketing"]
        V1["Partnership decision + management"]
        V2["FB pet groups (VN) — daily"]
        V3["TikTok filming (VI)"]
        V4["VN micro-KOL outreach"]
        V5["Zalo OA"]
        V6["Giveaway campaigns"]
        V7["Customer interviews (Mom Test)"]
        V8["Brand guidelines for partners"]
    end

    subgraph NGOC["Ngoc — Design"]
        N1["App Store screenshots (EN + VI)"]
        N2["Product Hunt graphics"]
        N3["Partner kit (if approved)"]
        N4["Social media templates"]
    end
```
