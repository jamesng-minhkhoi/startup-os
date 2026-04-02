# VocabX Growth Audit & Launch Playbook

**Date:** 2026-04-02
**Type:** Growth Engine Design + Launch Playbook
**Product:** VocabX (5-app vocabulary learning platform)
**Stage:** MVP-complete, pre-launch
**Operator:** Solo founder (bootstrapped)

---

# PART 1: GROWTH ENGINE DESIGN

---

## 1. North Star Metric

**North Star Metric: Weekly Active Learners who complete 3+ review sessions (WAL-3)**

Not DAU. Not downloads. Not revenue. WAL-3.

**Why this metric and not something else:**

| Candidate Metric | Why It Fails |
|---|---|
| Downloads | Vanity. Says nothing about product value. |
| DAU | Inflated by streak-only openers who tap once and leave. |
| Revenue/MRR | Lagging indicator. By the time revenue drops, users already churned weeks ago. |
| Streak count | Gameable. Users can maintain a streak with zero actual learning. |
| Words learned | Hard to define "learned." One quiz pass does not equal retention. |

**Why WAL-3 works:**

1. **Leading indicator of retention.** A user who reviews 3+ times per week is building a habit. Research on FSRS shows that 3 exposures/week is the minimum for long-term memory formation.
2. **Leading indicator of revenue.** Users who hit their free-tier limits (5 words/day, 5 reviews/day) 3+ times per week will feel the paywall naturally and convert.
3. **Leading indicator of referral.** Engaged learners are the ones who share. Nobody recommends an app they opened once.
4. **Actionable.** Every team decision can be tested against: "Does this increase WAL-3?"

**Metric tree:**

```
                    WAL-3 (Weekly Active Learners, 3+ sessions)
                    /           |            \
            New WAL-3      Retained WAL-3    Resurrected WAL-3
            /                   |                    \
    Activation Rate     Session Frequency      Re-engagement Rate
    /        \               |                       |
Onboarding   First        Review              Push notification
Completion   "Aha"        Reminders            win-back
             Moment
```

**Targets (first 90 days post-launch):**
- Month 1: 200 WAL-3
- Month 2: 500 WAL-3
- Month 3: 1,200 WAL-3

---

## 2. AARRR Funnel Design (Per Niche)

### Universal Funnel Structure

```
ACQUISITION --> ACTIVATION --> RETENTION --> REVENUE --> REFERRAL
App Store       First "aha"    Daily habit    Paywall     Share
search /        moment in      loop +         hit +       progress +
content /       < 90 sec       streak         convert     invite
referral                       economy                    friends
```

### 2A. IELTS Vocab (Recommended first launch -- see Part 2)

| Stage | Metric | Mechanism | Target |
|---|---|---|---|
| **Acquisition** | App Store impressions --> installs | ASO on "IELTS vocabulary," "IELTS word list," TikTok content targeting test-prep students, Reddit r/IELTS | 8% install rate |
| **Activation** | Install --> complete first quiz | Onboarding: "When is your IELTS exam?" --> personalized word count goal --> immediate 10-word quiz with score | 60% within first session |
| **Retention** | D1/D7/D30 return | Exam countdown timer ("87 days left, 2,400 words to learn"), daily push at study time, streak with exam-day stakes | D1: 40%, D7: 25%, D30: 12% |
| **Revenue** | Free --> paid conversion | Hard gate at 5 words/day for free. At day 3-4, user has seen ~15-20 words but needs 2,000+. Gap is visceral. Trial offer after 5th session. | 8% of MAU |
| **Referral** | Users who invite 1+ friend | "Study buddy" feature: share daily word with WhatsApp study group. Leaderboard among friends. | K-factor 0.15 |

**IELTS-specific insight:** This audience has a *deadline*. The exam date creates natural urgency that other niches lack. The countdown timer is the single most powerful retention mechanic for this niche. Every push notification should reference it: "67 days until your exam. You know 340 of 2,000 target words."

### 2B. MedVocab (Medical Terminology)

| Stage | Metric | Mechanism | Target |
|---|---|---|---|
| **Acquisition** | Installs from med student channels | Med school Facebook groups, Reddit r/medicalschool, Instagram study-gram, partnerships with anatomy YouTubers | 6% install rate |
| **Activation** | Install --> first "I didn't know that" moment | Onboarding: choose your year (pre-med, M1, M2, clinical). First feed shows terms from their current coursework. "Pericardium = peri (around) + cardium (heart)" breakdown. | 55% first-session completion |
| **Retention** | Weekly return rate | Exam-cycle alignment: push harder during anatomy block, ease off during breaks. "Your classmates reviewed 45 terms today" social proof. | D7: 22%, D30: 10% |
| **Revenue** | Free --> paid | At $14.99/mo, must demonstrate clear exam ROI. "Students who use MedVocab score 23% higher on terminology sections" (measure this internally). Anchor against $155/yr Picmonic. | 6% of MAU |
| **Referral** | Share to study group | "Share this week's term set with your anatomy study group" --> deep link to curated list | K-factor 0.2 |

### 2C. VocabX (General English)

| Stage | Metric | Mechanism | Target |
|---|---|---|---|
| **Acquisition** | Organic search + content | "Word of the day" TikTok/Reels, ASO on "vocabulary builder," "learn new words" | 7% install rate |
| **Activation** | Install --> save first word | Onboarding: "What's your goal?" (Sound smarter / Read better / Write better). Immediate feed of words matched to goal. First word they save = aha moment. | 50% |
| **Retention** | WAL-3 | Widget showing "word of the day" on home screen. Streak economy. Weekly "vocab score" report. | D7: 20%, D30: 8% |
| **Revenue** | Free --> paid | Softer paywall. Free tier feels complete but limited. Upsell on quiz variety, advanced analytics, unlimited saves. | 5% of MAU |
| **Referral** | Social sharing | "I just learned that 'defenestrate' means to throw someone out a window" -- shareable word cards for social media | K-factor 0.1 |

### 2D. Lexicon (Dark Academia)

| Stage | Metric | Mechanism | Target |
|---|---|---|---|
| **Acquisition** | Aesthetic-first social content | Dark academia TikTok, Tumblr, Pinterest boards, BookTok crossover | 10% install rate (niche = high intent) |
| **Activation** | Install --> fall in love with the aesthetic | Onboarding is the experience. Dark theme, serif fonts, parchment textures. First word: something like "petrichor" or "sonder." The app itself is the reward. | 65% |
| **Retention** | Collection completion | "Your Literary Lexicon: 47/500 words collected." Completion drive. Seasonal word sets (Gothic October, Romantic February). | D7: 28%, D30: 14% |
| **Revenue** | Free --> paid | Premium unlocks rare/obscure word collections, custom aesthetic themes, literary quote context for each word. This audience pays for identity. | 7% of MAU |
| **Referral** | Shareable aesthetic cards | Beautiful word cards designed for Instagram stories. "Add to your story" button. The share IS the product. | K-factor 0.25 |

### 2E. LegalLex (Legal Terminology)

| Stage | Metric | Mechanism | Target |
|---|---|---|---|
| **Acquisition** | Law school channels, LinkedIn | Reddit r/lawschool, LinkedIn legal community, law school orientation partnerships | 5% install rate |
| **Activation** | Install --> "This would have saved me hours" | Onboarding: select your courses (Contracts, Torts, ConLaw, etc.). First feed shows Latin legal terms with plain-English breakdowns. | 50% |
| **Retention** | Exam-cycle driven | Bar exam countdown (for bar prep users). Course-aligned review schedules. "Case brief vocab" tied to 1L reading assignments. | D7: 20%, D30: 9% |
| **Revenue** | Free --> paid | $14.99/mo anchored against $200+/mo bar prep courses. "Add LegalLex to your study stack for less than one casebook." | 6% of MAU |
| **Referral** | Study group sharing | Share term sets by course. "Share your Contracts I deck with your section." | K-factor 0.15 |

---

## 3. Retention Strategy: Beating the "2-Week Quit"

Education apps have the worst retention in all of mobile. Industry benchmarks: D1 ~15%, D7 ~8%, D30 ~2%. The "2-week cliff" is where most vocabulary apps die. Here is how VocabX survives it.

### The 2-Week Cliff: Why It Happens

```
Week 1: Novelty + motivation = daily usage
Week 2: Novelty fades. User realizes learning is work. 
         No visible progress. Skips a day. Then two. Then gone.
```

**Root causes:**
1. **No visible progress.** User has "learned" 50 words but can't feel smarter.
2. **No external accountability.** Nobody knows or cares if they quit.
3. **No sunk cost.** Nothing invested that would hurt to lose.
4. **Content sameness.** Day 14 feels identical to Day 1.

### The Anti-Churn Architecture (7 Layers)

**Layer 1: The Progress Cliff-Hanger (Days 1-3)**
- After onboarding, show the user their "vocabulary map" -- a visual representation of all words in their niche, with the tiny sliver they've started highlighted.
- End every session on a cliffhanger: "Tomorrow's word: ______ (a word that changes how you read contracts)." Curiosity gap = return.

**Layer 2: The Identity Shift (Days 3-7)**
- By day 3, start reflecting their progress back in identity terms:
  - "You're building a medical vocabulary. 3 days in a row."
  - "You now know more IELTS vocabulary than 40% of test-takers." (Benchmark against anonymized averages.)
- Users who see themselves as "someone who is building vocabulary" are 3x more likely to continue than users who see themselves as "someone trying an app."

**Layer 3: The Week 2 Intervention (Days 8-14) -- CRITICAL**
This is where most apps lose users. VocabX's specific interventions:

| Day | Trigger | Action |
|---|---|---|
| Day 8 | User has 7-day streak | Celebrate loudly. "7 days. Most people quit by now. You didn't." Award a milestone badge. |
| Day 10 | First missed day likely | If missed: immediate push -- "Your streak is still alive for 4 more hours. One quick review saves it." If not missed: "10 days. You're in the top 15% of learners." |
| Day 12 | Content fatigue likely | Unlock a NEW content type they haven't seen. If they've only done feed + review, unlock their first quiz game. Novelty injection. |
| Day 14 | The cliff | "2-week report" push: detailed analytics showing words learned, retention rate, estimated vocabulary growth. Make the invisible visible. |

**Layer 4: The Sunk-Cost Ladder (Ongoing)**
Make users invest progressively more so quitting feels expensive:
- Week 1: Save favorite words (low investment)
- Week 2: Create custom word lists (medium investment)
- Week 3: Build streak + earn achievements (high investment)
- Week 4: Compete on leaderboard, have study buddies (social investment)

Each layer makes leaving harder without feeling manipulative -- the user is building something genuinely valuable.

**Layer 5: Variable Session Length**
Not every session needs to be 10 minutes. VocabX should offer:
- **1-minute session:** Review 5 words on the widget without opening the app.
- **3-minute session:** Quick quiz (5 questions).
- **10-minute session:** Full feed browse + review + quiz.
- **"I have 30 seconds" session:** Single word card with swipe-to-save.

The key insight: a 30-second session that maintains the streak is infinitely better than a skipped day. Lower the floor, not the ceiling.

**Layer 6: Contextual Push Notifications (PostHog-powered)**
You already have 14 analytics events. Use them to trigger smart pushes:

| Event Pattern | Push Notification | Timing |
|---|---|---|
| User completed quiz with >80% score | "You're getting good at this. Ready for a harder set?" | Next morning |
| User browsed feed but didn't review | "You saved 3 new words yesterday. Quick review?" | 6 hours later |
| User missed 1 day (streak at risk) | "Your 12-day streak ends in 4 hours. 30-second review?" | 4 hours before midnight |
| User missed 2 days | "We saved your progress. 47 words waiting for review." | Morning of day 3 |
| User missed 7+ days | "Your vocabulary is fading. 3-minute refresh?" (Show a word they previously got right) | Once, then stop |

**Layer 7: The "Graduation" Problem**
Unique to education: users who succeed... leave. They learned the words. They passed the test. They're done.
- For IELTS/Medical/Legal: This is expected. Maximize revenue during the 3-6 month prep window. Don't fight it.
- For General/Lexicon: There is no graduation. Position as a lifelong practice, like a gym membership for your brain. "Your vocabulary is a muscle. Keep training."

### Retention Targets (Beating Industry Benchmarks)

| Metric | Industry Average (Education) | VocabX Target | How |
|---|---|---|---|
| D1 Retention | 14-15% | 40% | Onboarding aha moment + next-day cliffhanger |
| D7 Retention | 8% | 22% | Streak economy + identity reinforcement |
| D14 Retention | 4% | 15% | Week 2 intervention protocol + novelty injection |
| D30 Retention | 2% | 10% | Sunk-cost ladder + social features + variable sessions |

These targets are aggressive but achievable. Duolingo hits ~45% D1 and ~15% D30. You won't match Duolingo's scale, but you can match their retention mechanics in a focused niche.

---

## 4. The Hooked Model Applied to VocabX

Nir Eyal's Hooked model: **Trigger --> Action --> Variable Reward --> Investment.** Here is VocabX's hook cycle, designed to run multiple times per day.

### Hook Cycle 1: The Daily Word Feed

```
TRIGGER (External)                    TRIGGER (Internal)
Morning push notification:            "I feel like I should be
"Today's word: 'ameliorate'"          learning something"
         |                                    |
         v                                    v
                    ACTION
         Open app --> swipe through feed
         (Low friction: TikTok-style, 
          no decisions required, just swipe)
                        |
                        v
                 VARIABLE REWARD
    - Social: "You know more words than 73% of users"
    - Tribe: Word usage examples from real contexts
    - Self: "Aha!" moment -- "I've seen this word before 
      but never knew what it meant!"
    - Hunt: "What's the next word?" (Curiosity)
                        |
                        v
                   INVESTMENT
    - Save word to personal collection
    - Rate difficulty (feeds FSRS algorithm)
    - Streak counter increments
    - Progress bar fills slightly
    (Each investment improves the next trigger)
```

### Hook Cycle 2: The Review Loop

```
TRIGGER (External)                    TRIGGER (Internal)
Widget on home screen shows           "Did I actually remember 
a word due for review                  that word from yesterday?"
         |                                    |
         v                                    v
                    ACTION
         Tap widget --> 30-second review
         (Lowest possible friction)
                        |
                        v
                 VARIABLE REWARD
    - Self: Got it right! Memory confirmed.
    - Self: Got it wrong -- but now I'll remember 
      (FSRS reschedules optimally)
    - Hunt: "3 more words due today" (completion drive)
                        |
                        v
                   INVESTMENT
    - Review data improves FSRS accuracy
    - "Words mastered" counter increases
    - Achievement progress updates
```

### Hook Cycle 3: The Quiz Challenge

```
TRIGGER (External)                    TRIGGER (Internal)
Push: "Your weekly vocab quiz          "How much have I actually
is ready. Beat last week's score?"      learned this week?"
         |                                    |
         v                                    v
                    ACTION
         Take quiz (3-5 minutes, game-like)
                        |
                        v
                 VARIABLE REWARD
    - Self: Score reveal (dopamine hit or learning moment)
    - Social: Rank vs. other users
    - Hunt: "You missed 2 words. Review them now?"
    - Mastery: Badge earned for quiz streaks
                        |
                        v
                   INVESTMENT
    - Quiz history builds personal analytics
    - Weak words flagged for extra review
    - Quiz streak started (new commitment)
```

### Internal Trigger Development Timeline

The goal is to move from external triggers (push notifications) to internal triggers (feelings/habits):

| Week | Primary Trigger | Internal Trigger Forming |
|---|---|---|
| 1 | Push notifications, app store novelty | None yet |
| 2-3 | Push notifications, streak fear | "I should check my streak" |
| 4-6 | Streak fear, review reminders | "I wonder what today's word is" |
| 7-12 | Habit cue (morning routine) | "I feel weird if I don't review" |
| 12+ | Internal habit | "This is what I do. I build my vocabulary." |

---

## 5. Growth Loops

Growth loops are self-reinforcing cycles where the output of one cohort becomes the input for the next. VocabX has 4 viable loops.

### Loop 1: Content Loop (Highest Priority)

```
User learns interesting word
        |
        v
User shares word card on social media
(Beautiful, branded, designed for sharing)
        |
        v
Follower sees card, thinks "I want to learn words like that"
        |
        v
Follower downloads app (UTM-tracked deep link)
        |
        v
New user learns interesting word...
```

**Implementation:**
- Every word card has a "Share" button that generates a beautiful image with: the word, its definition, a usage example, and the VocabX logo + "Learn more at vocabx.app"
- For Lexicon specifically: the share cards should be so aesthetically beautiful that people share them even without the app. Dark backgrounds, serif fonts, gold accents. Think Pinterest-worthy.
- For IELTS: share cards show "IELTS Band 7+ Vocabulary" branding. Test-prep students share study resources compulsively.
- Track: shares per WAL, installs per share, activation rate of shared-link users.

**Estimated K-factor contribution: 0.05-0.15**

### Loop 2: UGC/SEO Loop (Medium Priority, Long-Term)

```
User creates custom word list ("100 words for IELTS Speaking")
        |
        v
List is public (opt-in) and indexed by search engines
        |
        v
Google searcher finds "IELTS speaking vocabulary list"
        |
        v
Lands on web page, prompted to download app for FSRS review
        |
        v
New user creates their own lists...
```

**Implementation (post-launch, Month 3+):**
- Build a simple web view for public word lists.
- Each list has meta tags optimized for its topic.
- Users who create lists feel ownership and stay longer (investment from Hooked model).
- This is how Quizlet grew: user-generated study sets became SEO goldmines.

**Timeline: Build in Month 3-4. SEO results in Month 6+.**

### Loop 3: Study Group Loop (For IELTS, Medical, Legal)

```
User joins/creates study group in-app
        |
        v
User invites classmates via WhatsApp/iMessage link
        |
        v
Classmates download app to join group
        |
        v
Group creates social accountability (retention boost)
        |
        v
Group members invite MORE classmates...
```

**Implementation:**
- "Study with friends" feature: share a group code or deep link.
- Group leaderboard: who reviewed the most this week?
- Shared progress: "Your study group has learned 1,247 words together."
- For IELTS: "IELTS Study Group" with shared exam date countdown.
- For Medical: "Anatomy Block Study Group" aligned to coursework.

**Estimated K-factor contribution: 0.1-0.2**

### Loop 4: Achievement/Status Loop

```
User earns achievement ("500 Words Mastered")
        |
        v
Achievement generates shareable badge/card
        |
        v
Shared to LinkedIn (professional), Instagram (lifestyle), 
Twitter (intellectual flex)
        |
        v
Connections/followers see badge, ask "What app is this?"
        |
        v
New download...
```

**Implementation:**
- Achievement milestones: 100, 500, 1000, 2500, 5000 words mastered.
- Streak milestones: 7, 30, 100, 365 days.
- Each milestone generates a share-ready graphic.
- For Medical/Legal: LinkedIn-optimized badges ("I've mastered 500 medical terms with MedVocab").
- For Lexicon: Instagram-optimized aesthetic badges.

### Growth Loop Priority Matrix

| Loop | Effort | Impact | Timeline | Priority |
|---|---|---|---|---|
| Content (share cards) | Low | Medium | Immediate | P0 -- must ship at launch |
| Study Groups | Medium | High (for niche apps) | Month 2 | P1 |
| Achievement Sharing | Low | Low-Medium | Month 1 | P1 |
| UGC/SEO | High | High (long-term) | Month 3-6 | P2 |

---

## 6. The Streak Economy: Making Streaks Actually Work

Most apps implement streaks badly. The streak becomes a vanity number that users game (open app, close app, streak maintained) or abandon after one missed day. Here is how to make streaks a genuine retention engine.

### Problem: Why Most Streaks Fail

1. **Binary fragility.** Miss one day, lose everything. Users who lose a 30-day streak rarely come back -- the loss aversion is too painful, so they quit entirely.
2. **No graduation.** Day 365 feels the same as Day 7. No progression.
3. **Gameable.** Users open the app for 2 seconds to "maintain" the streak. No learning happens.
4. **No social proof.** Streaks are invisible to others.

### VocabX Streak Architecture

**Rule 1: Streaks require minimum activity, not just app opens.**
A streak day is only counted when the user completes at least one of:
- 3 word reviews
- 1 quiz
- 5 feed swipes with at least 1 save

This prevents gaming. The user must actually engage.

**Rule 2: Streak Shields (anti-fragility).**
- Every 7-day streak earns 1 "Streak Shield" (max stockpile: 3).
- A Streak Shield automatically covers 1 missed day.
- This means a user with a 21-day streak has 3 shields and can miss up to 3 days without breaking.
- Premium users get 1 bonus shield per month.
- This converts the devastating "I broke my streak, I quit" moment into "Phew, my shield saved me. I should review today."

**Rule 3: Streak Tiers (graduation, not just counting).**

| Streak Length | Tier Name | Visual | Unlock |
|---|---|---|---|
| 3 days | Spark | Small flame | Nothing -- just starting |
| 7 days | Ember | Growing flame | 1 Streak Shield earned |
| 14 days | Blaze | Medium flame + glow | Achievement badge shareable |
| 30 days | Inferno | Large flame + particles | Unlock bonus word pack |
| 60 days | Wildfire | Animated flame | Custom app icon |
| 100 days | Eternal Flame | Premium animation | Hall of Fame listing |
| 365 days | Vocabulary Immortal | Full-screen celebration | Lifetime badge on profile |

**Rule 4: Streak Wagers (borrowed from Duolingo's 14% retention lift).**
- At day 7, offer: "Bet 50 XP that you'll maintain your streak for 7 more days. Win = 100 XP back."
- Users who wager show 14% higher D14 retention (Duolingo data).
- The wager creates a micro-commitment that makes the next 7 days feel like a challenge, not a chore.

**Rule 5: Social Streak Visibility.**
- Show streak flames on user profiles in study groups.
- Weekly push: "3 people in your study group have longer streaks than you."
- Streak leaderboard in study groups (not global -- global feels unbeatable).

**Rule 6: Streak Recovery (don't punish, re-engage).**
- If a user breaks their streak (and has no shields):
  - Don't reset to 0 silently. Show: "Your 23-day streak paused. Start a new one today and you'll earn a 'Comeback' badge at day 7."
  - Offer a "streak repair" for premium users (restore the streak if they complete 2x the normal activity today).
- The goal: make breaking a streak feel like a setback, not a catastrophe.

---

## 7. Referral Mechanics: Making Vocabulary Learning Social

Vocabulary learning is inherently individual. The referral challenge is: *why would someone invite a friend to a vocabulary app?* Here are mechanics that give users a genuine reason.

### Mechanic 1: "Word Battles" (1v1 Vocabulary Duels)

- User challenges a friend to a real-time vocabulary quiz.
- Both receive the same 10 words. Fastest correct answers win.
- Friend needs the app to accept the challenge (install gate).
- Winner gets XP + bragging rights.
- **Why it works:** Competitive friends will play repeatedly. "I bet you don't know what 'sycophant' means" is a natural flex.

### Mechanic 2: "Study Buddy" Referral

- Invite a friend --> both get 7 days of premium free.
- If friend converts to paid, referrer gets 1 month free.
- Cap at 3 referral rewards (prevents abuse, keeps it sustainable).
- **Why it works:** Direct value exchange. Simple. Proven.

### Mechanic 3: "Share Your Score" Post-Quiz

- After every quiz, show a shareable results card: "I scored 9/10 on Advanced Medical Terminology. Can you beat me?"
- Deep link takes the challenger directly to the same quiz.
- **Why it works:** Quizzes are inherently shareable. People love showing off knowledge.

### Mechanic 4: "Word of the Day" Group Share

- Users can set up a daily "Word of the Day" push to a WhatsApp/iMessage group.
- Each word links back to the app for full definition, examples, and review.
- **Why it works:** Low-friction daily touchpoint that puts VocabX branding in front of potential users. Especially powerful for IELTS study groups already on WhatsApp.

### Referral Targets

| Niche | Primary Referral Mechanic | Target K-Factor |
|---|---|---|
| IELTS Vocab | WhatsApp study group share | 0.15 |
| MedVocab | Study group invite + score sharing | 0.2 |
| VocabX General | Word battles + social word cards | 0.1 |
| Lexicon | Aesthetic share cards (passive) | 0.25 |
| LegalLex | Study group invite | 0.15 |

**K-factor reality check:** A K-factor above 0.3 is rare for non-social apps. Anything above 0.1 meaningfully reduces your CAC. Don't chase virality -- chase consistent, small-scale word-of-mouth.

---

## 8. Churn Prevention: Triggers, Signals, and Interventions

### The 6 Churn Triggers in Education Apps

| Trigger | Signal in PostHog | Intervention |
|---|---|---|
| **1. No early aha moment** | User installs but never completes a quiz or saves a word in session 1 | Redesign onboarding. Force the aha moment: show them a word they've seen but can't define, then teach it. "See? You already needed this." |
| **2. Content mismatch** | User browses feed but difficulty rating is consistently "too easy" or "too hard" | Adaptive difficulty. If 3+ words in a row are rated easy, jump to advanced tier. If 3+ are rated hard, drop down. FSRS handles this for reviews; extend it to feed content. |
| **3. Streak break despair** | User had 10+ day streak, breaks it, doesn't open app for 48+ hours | Streak Shield (see Section 6). If no shield: "Comeback" push notification at 48 hours with streak repair offer. |
| **4. Paywall frustration** | User hits free-tier limit 3+ times but doesn't convert | Re-evaluate gate timing. Are they hitting the wall too early (before aha) or too late (already bored)? Test: move paywall trigger to after the user's 5th quiz, not 5th word. |
| **5. Plateau feeling** | User's "words mastered" count slows (expected -- FSRS shows diminishing returns on easy words) | Introduce new content types at plateaus: etymology deep-dives, word origin stories, "words in the wild" (real-world usage examples). Break monotony. |
| **6. Life event disruption** | User goes from daily usage to zero for 7+ days (exams, travel, illness) | Grace period + gentle re-engagement. Day 7: "We kept your progress safe. Pick up where you left off with a 2-minute review." Day 14: "Your vocabulary might be fading. Here's a word you mastered last month -- do you still remember it?" Day 30: Last attempt, then stop. Never spam someone who left. |

### Churn Prediction Model (PostHog-powered)

With 14 analytics events already wired, build a simple churn risk score:

```
Churn Risk Score (0-100) =
  + 20 if no session in last 48 hours
  + 15 if session length trending down (3-session moving average)
  + 15 if quiz scores declining
  + 10 if no word saves in last 3 sessions
  + 10 if push notification open rate < 10% (last 5 pushes)
  + 10 if streak broke and no recovery within 24 hours
  + 10 if free-tier limit hit 3+ times without conversion
  + 10 if never used review feature
```

**Actions by risk tier:**

| Risk Score | Tier | Action |
|---|---|---|
| 0-20 | Healthy | Normal experience. No intervention needed. |
| 21-40 | At Risk | Increase push notification value (word previews, quiz teasers). Surface new content types. |
| 41-60 | Danger | Streak Shield reminder. Personal "we miss you" push. Offer extended free trial if not yet converted. |
| 61-80 | Critical | Win-back email with "Here's what you've learned so far" summary. One-time discount offer. |
| 81-100 | Lost | Single final push: "Your progress is saved. Come back anytime." Then silence. Respect the user's choice. |

---

# PART 2: LAUNCH PLAYBOOK

---

## 1. Which App Launches First?

**Recommendation: IELTS Vocab.**

Not VocabX General. Not Lexicon. IELTS Vocab.

### Reasoning

| Factor | IELTS Vocab | VocabX General | Lexicon | MedVocab | LegalLex |
|---|---|---|---|---|---|
| **Market urgency** | Exam deadline = must-have | Nice-to-have | Nice-to-have | Semester-driven | Semester-driven |
| **Market size** | $11B+ platform market, 12M+ app downloads, 2.8M candidates/year | Massive but diffuse | Small niche | Medium, specialized | Small niche |
| **Willingness to pay** | HIGH -- students already spend $100-300+ on prep | Low -- free alternatives abundant | Medium -- identity purchase | Medium-High | Medium-High |
| **ASO competition** | Moderate -- established players but keyword-rich | Brutal -- Duolingo, Wordly, etc. | None (blue ocean) | Low-Medium | Low |
| **Content marketing angle** | "IELTS vocabulary" is a searchable, specific pain point | Generic, hard to stand out | Aesthetic but small | Specialized | Specialized |
| **Retention mechanics** | Exam countdown = built-in urgency | Must manufacture urgency | Collection drive | Exam-driven | Exam-driven |
| **Referral potential** | WhatsApp study groups = natural viral channel | Low | Medium (aesthetic sharing) | Medium (study groups) | Medium |
| **Revenue per user** | $9.99/mo x 3-6 month prep cycle = $30-60 LTV | $9.99/mo x uncertain tenure | $9.99/mo x medium | $14.99/mo x higher | $14.99/mo x higher |

**The decisive factor:** IELTS test-takers are the only audience with a non-negotiable deadline and a proven willingness to pay for test prep. They search for solutions actively ("IELTS vocabulary app"), they share resources in WhatsApp groups naturally, and they have a defined prep window (3-6 months) that creates predictable revenue.

General English (VocabX) sounds broader, but "broader" means "competing with Duolingo for users who aren't sure why they're here." Start narrow. Win a beachhead. Expand.

**Launch order:**
1. **IELTS Vocab** (Week 1 -- your pathfinder)
2. **MedVocab** (Week 4-6 -- second high-intent niche)
3. **Lexicon** (Week 8-10 -- test the aesthetic/identity market)
4. **LegalLex** (Week 12 -- complete the professional suite)
5. **VocabX General** (Week 16+ -- launch last, with social proof from niche apps)

---

## 2. Pre-Launch Checklist (IELTS Vocab)

### App Store Readiness (Week -2 to -1)

- [ ] **Apple Developer Account** active and paid ($99/year).
- [ ] **App Store Connect** listing created for "IELTS Vocab."
- [ ] **App Review Guidelines** compliance check: no misleading claims about test scores, clear subscription terms, privacy policy URL live.
- [ ] **RevenueCat** products configured: monthly ($9.99), annual ($79.99 -- 33% discount), 7-day free trial on annual only.
- [ ] **Privacy policy** and **Terms of Service** pages live (can be simple hosted pages on your domain).
- [ ] **App icon** finalized: clean, recognizable at small size, distinct from Duolingo green. Recommend: deep blue/navy with a clean "IELTS" mark.
- [ ] **Screenshots** (6 required, iPhone 6.7" and 6.5" at minimum): see ASO section below for concepts.
- [ ] **App Preview Video** (optional but recommended): 15-30 second screen recording showing the TikTok-style feed + quiz in action.
- [ ] **TestFlight build** submitted and running clean on iOS 17+.
- [ ] **Crash reporting** active (Sentry or equivalent alongside PostHog).
- [ ] **PostHog** 14 events verified firing correctly in production build.
- [ ] **Push notification** certificate configured and tested (APNs).
- [ ] **Offline cache** verified: app works on airplane mode for previously loaded content.
- [ ] **Widget** tested on multiple iPhone models (small, medium, large sizes).

### Content Readiness

- [ ] **Minimum 500 IELTS vocabulary words** loaded in Supabase with: word, definition, pronunciation guide, example sentence, IELTS context (Academic/General Training), difficulty tier (Band 5-6, 6-7, 7-8, 8-9).
- [ ] **20+ quiz questions** per difficulty tier ready.
- [ ] **FSRS parameters** calibrated with test data (default FSRS-5 parameters are fine for launch; they self-calibrate with user data).
- [ ] **Word feed** algorithm tested: new users see Band 5-6 words first, difficulty increases with usage.

### Marketing Readiness

- [ ] **Landing page** live: ieltsvocab.app (or similar) with email capture, App Store badge (add after approval), 3 key screenshots, social proof placeholder.
- [ ] **Social accounts** created: TikTok (@ieltsvocab), Instagram (@ieltsvocab), Reddit account for r/IELTS participation.
- [ ] **5 TikTok/Reels videos** pre-recorded and ready to post (see Content Strategy section).
- [ ] **Email sequence** drafted: 3 pre-launch emails for waitlist (see Email section).
- [ ] **r/IELTS participation** started: answer vocabulary questions genuinely for 2+ weeks before launch. Build credibility, not spam.
- [ ] **10 beta testers** recruited from IELTS communities: real feedback, plus launch-day reviews.

### Technical Readiness

- [ ] **273 tests passing** -- confirmed.
- [ ] **Load testing**: can Supabase handle 1,000 concurrent users? (It can at the free tier for read-heavy workloads, but verify.)
- [ ] **Deep links** working: social share cards link to App Store listing.
- [ ] **Attribution tracking**: UTM parameters flowing from social --> App Store --> PostHog.
- [ ] **Rate limiting** on API calls to prevent abuse of free tier.

---

## 3. ASO Strategy: IELTS Vocab

### App Name and Subtitle

**App Name (30 char max):** `IELTS Vocab - Word Builder`

**Subtitle (30 char max):** `Band 7+ Vocabulary & Quizzes`

**Reasoning:** "IELTS" is the primary keyword -- it must be in the title. "Vocab" is the secondary keyword. "Band 7+" signals the target level (most test-takers aim for 7+). "Word Builder" adds a secondary keyword for non-IELTS searches.

### Keywords Field (100 characters, comma-separated, no spaces after commas)

```
ielts,vocabulary,english,test,prep,words,study,flashcards,speaking,writing,academic,band,score,learn
```

**Keyword strategy:**
- Primary: ielts, vocabulary, english test
- Secondary: flashcards, study, learn english, word
- Long-tail (via title+keyword combo): "ielts vocabulary," "ielts word builder," "ielts band 7 vocabulary"
- Excluded (too competitive): "language learning," "english learning app" (Duolingo owns these)

### Description (4,000 char max)

```
Master the vocabulary you need for IELTS Band 7 and above.

IELTS Vocab uses the same spaced repetition algorithm trusted by millions 
of Anki users (FSRS) to help you remember every word permanently -- not 
just for test day.

HOW IT WORKS
Swipe through new vocabulary in a TikTok-style word feed. Each word 
includes the definition, pronunciation, example sentence, and IELTS 
context (Speaking, Writing, Reading, or Listening). Save words you want 
to learn, and our algorithm schedules your reviews at the perfect moment 
for long-term memory.

FEATURES
- 2,000+ IELTS vocabulary words organized by band score (5-6, 6-7, 7-8, 8-9)
- Spaced repetition reviews powered by FSRS (the algorithm behind Anki)
- Quiz games to test your knowledge under pressure
- Daily streaks and achievements to keep you motivated
- Exam countdown timer -- see exactly how many words you need to learn per day
- iOS home screen widget for quick daily reviews
- Works offline -- study anywhere, even without internet
- Track your progress with detailed vocabulary analytics

FREE PLAN
- Learn 5 new words per day
- 5 spaced repetition reviews per day
- 1 quiz per day
- Full access to Band 5-6 vocabulary

PREMIUM ($9.99/month)
- Unlimited words, reviews, and quizzes
- All band levels (5-9)
- Advanced quiz modes
- Priority word recommendations based on your weak areas
- Streak shields to protect your progress

Built by an IELTS vocabulary specialist. No generic word lists -- every 
word is selected because it appears in real IELTS exams.

Start your free plan today. Your exam is coming. Your vocabulary 
shouldn't hold you back.
```

### Screenshot Concepts (6 screenshots)

| # | Concept | Top Caption | What It Shows |
|---|---|---|---|
| 1 | Hero shot | "Master IELTS Vocabulary" | TikTok-style word feed showing a Band 7 word with definition + example. Clean, professional UI. |
| 2 | Spaced repetition | "Remember Every Word" | Review screen with FSRS scheduling visual: "Next review: 3 days." Shows the memory curve. |
| 3 | Quiz game | "Test Under Pressure" | Quiz screen with multiple-choice question, timer, score. Feels game-like. |
| 4 | Progress tracking | "Track Your Band Score Progress" | Analytics screen: words mastered by band, vocabulary growth chart, exam countdown. |
| 5 | Streak & achievements | "Build Unstoppable Momentum" | Streak flame at 14 days, 3 achievement badges earned, streak shield icon. |
| 6 | Widget | "Learn on Your Home Screen" | iPhone home screen with IELTS Vocab widget showing word of the day. Real-world context. |

**Design guidelines:**
- Background color: deep navy or dark blue (IELTS brand association + premium feel).
- Device frame: latest iPhone.
- Font: clean sans-serif, white text on colored backgrounds.
- No more than 6 words in the top caption.
- Show real UI, not mockups. Reviewers and users can tell the difference.

### Category Selection

- **Primary category:** Education
- **Secondary category:** Reference

---

## 4. Content Strategy: First 90 Days

### Content Pillars

| Pillar | What | Where | Frequency |
|---|---|---|---|
| **Word of the Day** | Single IELTS word with definition, example, and "Did you know?" context | TikTok, Instagram Reels, Instagram Stories | Daily |
| **Quiz Challenge** | "Can you get 5/5?" short quiz video | TikTok, Instagram Reels | 3x/week |
| **IELTS Tips** | Speaking/Writing tips featuring vocabulary usage | TikTok, YouTube Shorts | 2x/week |
| **Community Answers** | Answer real IELTS vocabulary questions from Reddit/forums | Reddit r/IELTS, Quora | Daily (comments, not posts) |
| **Progress Stories** | "Day 30 of learning IELTS vocab" building-in-public series | TikTok, Instagram | Weekly |

### 90-Day Content Calendar

**Days 1-30: Foundation (Pre-launch + Launch Week)**

| Week | Focus | Content Pieces | Platform Priority |
|---|---|---|---|
| Week 1 | Pre-launch buzz | 5 "Word of the Day" TikToks, 3 Reddit answers in r/IELTS, landing page live | TikTok, Reddit |
| Week 2 | Launch week | Launch announcement TikTok, "Day 1" progress post, 5 Word of the Day, 2 Quiz Challenges | TikTok, Instagram, Reddit |
| Week 3 | Post-launch momentum | 5 Word of the Day, 3 Quiz Challenges, 2 IELTS Tips, daily Reddit engagement | TikTok, Instagram |
| Week 4 | First testimonials | Feature beta tester quotes, "1,000 words reviewed" milestone, continue daily content | TikTok, Instagram |

**Days 31-60: Growth**

| Week | Focus | Content Pieces |
|---|---|---|
| Week 5-6 | Series content | Launch "5 Words Every IELTS Speaker Needs" multi-part series (3-5 episodes). Start YouTube Shorts reposts. |
| Week 7-8 | Community building | Feature user scores/streaks (with permission). "Study group spotlight." Start Instagram carousel posts with 5-word vocabulary sets. |

**Days 61-90: Optimization**

| Week | Focus | Content Pieces |
|---|---|---|
| Week 9-10 | Double down on winners | Review analytics. Which content format got the most views/engagement? 2x that format. Cut what didn't work. |
| Week 11-12 | Prep for MedVocab launch | Begin medical vocabulary teaser content. Continue IELTS content on autopilot with established formats. |

### Platform-Specific Strategy

**TikTok (Primary -- 80% of effort):**
- Post 1-2x per day.
- Use trending sounds when applicable, but educational content performs fine without them.
- Always include captions/subtitles (IELTS audience is non-native English speakers).
- Hook in first 1 second: show the word on screen immediately.
- Hashtags: #IELTS #IELTSprep #IELTSvocabulary #EnglishLearning #LearnEnglish #vocabulary

**Instagram (Secondary -- 15% of effort):**
- Repost TikToks as Reels.
- Add carousel posts (static vocabulary sets) -- these get saved/shared more.
- Use Stories for daily word of the day with poll ("Did you know this word? Yes/No").

**Reddit (Tertiary -- 5% of effort, but critical for credibility):**
- Never self-promote directly. Answer questions, provide value.
- After 2+ weeks of genuine participation, occasional mention: "I actually built an app for this exact problem" is acceptable.
- Subreddits: r/IELTS (290k+), r/EnglishLearning (700k+), r/languagelearning (1.3M+).

---

## 5. TikTok/Reels Repeatable Content Formats

VocabX needs its own "Is This Safe?" -- a repeatable format that's easy to produce, endlessly variable, and triggers saves/shares. Here are 5 formats, ranked by expected performance.

### Format 1: "Do You Actually Know This Word?" (Primary Format)

```
HOOK (0-1 sec): Word appears on screen in large text. "UBIQUITOUS"
QUESTION (1-3 sec): "Most people use this word wrong. Do you know 
                      what it actually means?"
WRONG ANSWER (3-5 sec): "Common guess: 'unique' or 'special'" 
                         (show wrong definition with X)
REVEAL (5-8 sec): "It actually means 'present everywhere.' 
                    WiFi is ubiquitous. Starbucks is ubiquitous."
IELTS CONTEXT (8-12 sec): "IELTS Band 8 word. Use it in Writing Task 2: 
                            'Social media has become ubiquitous in 
                            modern society.'"
CTA (12-15 sec): "Save this. Follow for daily IELTS words."
```

**Why it works:**
- The "most people get this wrong" hook triggers ego/curiosity (people want to prove they know it).
- Short enough to watch multiple times.
- Naturally saves/shares -- people save vocabulary posts.
- Endlessly repeatable -- there are thousands of words.
- Production time: 10-15 minutes per video.

### Format 2: "Word Tier List" (Weekly)

```
HOOK: "Ranking IELTS vocabulary by how much they'll boost your score"
CONTENT: Show 5-8 words being ranked S/A/B/C tier on a tier list graphic.
         Quick explanation for each: "MITIGATE -- S tier. Examiners love 
         this in Writing Task 2."
CTA: "What tier would you put 'ELABORATE'? Comment below."
```

**Why it works:** Tier lists are a proven TikTok format. They drive comments (disagreement = engagement). They're educational and entertaining simultaneously.

### Format 3: "What This Word Actually Means" (3x/week)

```
HOOK: Show a commonly misused/misunderstood word.
CONTENT: "LITERALLY doesn't mean what you think it means..."
         Show the actual definition vs. common misuse.
         Give the IELTS-appropriate usage.
CTA: "Follow for words that actually boost your IELTS score."
```

### Format 4: "Quiz Me" Interactive (2x/week)

```
HOOK: "Can you get 5/5? IELTS Vocabulary Quiz"
CONTENT: Show 5 words one by one. Pause 2 seconds on each. 
         Show 3 multiple-choice options. Then reveal the answer.
CTA: "Comment your score. 5/5 = you're ready for Band 8."
```

**Why it works:** Interactive content drives watch time (users pause to think). Comments section becomes a community. "Comment your score" is a proven engagement driver.

### Format 5: "Replace This Basic Word" (2x/week)

```
HOOK: "Stop saying 'GOOD' in your IELTS essay"
CONTENT: "Instead, say: EXEMPLARY (Band 7), COMMENDABLE (Band 7), 
         SUPERLATIVE (Band 8), UNPARALLELED (Band 8)"
         Show each word with a quick definition and example sentence.
CTA: "Save this list. Your examiner will notice."
```

**Why it works:** Directly actionable. Users save these for exam prep. "Stop saying X" is a proven hook formula.

### Production Workflow (Solo Founder)

| Step | Tool | Time |
|---|---|---|
| Script | Write 5 scripts in a batch (Sunday) | 45 min |
| Record | Face-to-camera or screen recording with voiceover | 10 min each |
| Edit | CapCut (free, mobile) -- add text overlays, captions | 10 min each |
| Post | TikTok native upload, cross-post to Instagram Reels | 5 min each |
| **Total per week** | | **~4 hours for 7 videos** |

---

## 6. Email/Waitlist Sequence

### Waitlist Capture (Pre-Launch Landing Page)

**Page elements:**
- Headline: "Master IELTS Vocabulary. Score Band 7+."
- Subheadline: "2,000+ words with spaced repetition. Free plan available."
- Email input + "Join the waitlist" button.
- Below the fold: 3 screenshots, "How it works" in 3 steps, "Launching [month]."
- Optional: "When is your IELTS exam?" date picker (use this data for personalized launch email).

### Pre-Launch Email Sequence (3 emails)

**Email 1: Welcome (Immediate)**
```
Subject: You're in. Here's a free IELTS word to start.

Hey [name],

You're on the IELTS Vocab waitlist. Here's your first word:

AMELIORATE (v.) -- to make something better
Band level: 8
Example: "The new policy aims to ameliorate living conditions 
in urban areas."
Use it in: Writing Task 2, Speaking Part 3

I'm building this app because I believe vocabulary is the 
easiest Band score lever -- and nobody has built a great 
vocab app specifically for IELTS.

More soon.

[Your name]
Founder, IELTS Vocab
```

**Email 2: Value + Social Proof (Day 3)**
```
Subject: The 200-word shortcut to IELTS Band 7

Most IELTS prep courses throw 3,000 words at you. 

Here's what they don't tell you: Band 7 requires roughly 
200 specific high-frequency academic words that appear 
across Reading, Writing, and Listening.

IELTS Vocab identifies exactly which words give you the 
most band-score leverage and uses the FSRS algorithm (the 
same one behind Anki) to schedule your reviews perfectly.

[Beta tester name] went from Band 6 to 7 vocabulary scores 
in 6 weeks using our early version.

Launch is [date]. You'll be first to know.

[Your name]
```

**Email 3: Launch Day (Launch Day)**
```
Subject: IELTS Vocab is live. Start free today.

It's here.

IELTS Vocab is now on the App Store.

- 2,000+ IELTS words organized by band score
- Spaced repetition that actually works (FSRS algorithm)
- Quiz games to test under pressure
- Free plan: 5 words/day, 5 reviews/day, 1 quiz/day

[Download on the App Store -- button/link]

As a waitlist member, you can also grab 30% off your first 
3 months of Premium with code EARLYBIRD.

Your exam is coming. Don't let vocabulary hold you back.

[Your name]
```

### Post-Launch Nurture (For users who download but don't convert)

**Day 3 post-install:**
```
Subject: You've learned [X] words this week

You've been using IELTS Vocab for 3 days. Here's your progress:
- [X] new words learned
- [X] reviews completed  
- Current streak: [X] days

At this pace, you'll know [projected number] words by your exam date.

Want to accelerate? Premium unlocks unlimited words and all band levels.

[Upgrade link]
```

**Day 7 post-install (if still free):**
```
Subject: What Band 7+ students do differently

The students who score Band 7+ don't study more words. 
They review more consistently.

Your FSRS algorithm has identified [X] words you're about 
to forget. A 3-minute review session will lock them in.

[Open IELTS Vocab]

P.S. Premium users get unlimited reviews. Free trial available.
```

---

## 7. Launch Day Runbook (Solo Founder)

### T-Minus 3 Days

- [ ] Final TestFlight build verified on 3+ real devices.
- [ ] Submit to App Store Review (allow 24-48 hours; submit early).
- [ ] Draft all launch day social posts (TikTok, Instagram, Reddit, Twitter).
- [ ] Pre-schedule emails in your email tool (Loops, Resend, or Mailchimp).
- [ ] Alert beta testers: "App goes live on [date]. Please leave an honest review on launch day."
- [ ] Prepare a "launch day" TikTok video showing the app going live.

### T-Minus 1 Day

- [ ] Confirm app is "Ready for Sale" in App Store Connect.
- [ ] Verify RevenueCat products are live and purchasable.
- [ ] Test the full flow: download from App Store --> onboarding --> free usage --> paywall --> purchase --> premium access.
- [ ] Verify PostHog events firing in production.
- [ ] Verify push notifications working.
- [ ] Get a good night's sleep. Seriously.

### Launch Day Schedule

| Time | Action | Duration |
|---|---|---|
| **7:00 AM** | Confirm app is live on App Store. Download it yourself. Run through the flow. | 15 min |
| **7:30 AM** | Send launch email to waitlist. | 5 min |
| **8:00 AM** | Post launch TikTok (pre-recorded). Cross-post to Instagram Reels. | 10 min |
| **8:15 AM** | Post to Reddit r/IELTS (not as a promotion -- as a "I built this, feedback welcome" post). | 10 min |
| **8:30 AM** | Post to Twitter/X with App Store link + screenshot. | 5 min |
| **8:30-12:00** | Monitor: respond to every comment, every DM, every review. This is your highest-leverage activity today. | 3.5 hours |
| **12:00 PM** | Check PostHog: how many installs? How many completed onboarding? Any crashes? | 15 min |
| **12:30 PM** | Post a second TikTok: "Word of the Day" in your normal format (don't over-index on launch; keep the content rhythm going). | 15 min |
| **1:00-5:00 PM** | Continue monitoring and responding. Fix any bugs immediately. | 4 hours |
| **5:00 PM** | Instagram Story: "Day 1 stats" (downloads, reviews, first user milestones). Building-in-public transparency. | 10 min |
| **6:00 PM** | Post to any IELTS Facebook groups you're a member of (genuine, not spammy). | 15 min |
| **8:00 PM** | End-of-day PostHog review: installs, activations, first-session completion, any errors. | 30 min |
| **8:30 PM** | DM/email 5 people who downloaded and ask: "How was it? What confused you?" Direct feedback. | 20 min |
| **9:00 PM** | Write down your 3 biggest learnings from launch day. What to change tomorrow. | 15 min |

### Launch Day Emergency Playbook

| Emergency | Action |
|---|---|
| App crashes on launch | Hotfix immediately. If un-fixable in 2 hours, pull the build and resubmit. Post on social: "We found a bug, fix coming in [X] hours." Honesty > silence. |
| App Store rejection | Read the rejection reason carefully. Most common: missing privacy policy, misleading screenshots, unclear subscription terms. Fix and resubmit same day. |
| Zero downloads | Don't panic. Day 1 downloads are heavily dependent on your existing audience. Focus on content and community engagement. Growth is a marathon. |
| Negative reviews | Respond to every 1-2 star review publicly in App Store Connect. "Thank you for the feedback. Can you email me at [email] so I can fix this for you?" Turns critics into advocates. |
| Supabase goes down | Free-tier Supabase has uptime SLAs, but if it happens: the offline cache should keep the app functional. Users can still review cached words. |

---

## 8. Success Metrics: Day 1/7/30 Targets

### Realistic Targets for a Solo Founder Launch (No Paid Ads)

These targets assume: a 200-person email waitlist, 500+ TikTok followers from pre-launch content, active Reddit participation, and zero ad spend.

| Metric | Day 1 | Day 7 | Day 30 | Day 90 |
|---|---|---|---|---|
| **Downloads** | 50-100 | 200-400 | 500-1,200 | 2,000-5,000 |
| **D1 Retention** | -- | 35-45% | Stabilize at 40% | 40%+ |
| **D7 Retention** | -- | -- | 20-25% | 22-28% |
| **D30 Retention** | -- | -- | -- | 8-12% |
| **Onboarding Completion** | 60%+ | 60%+ | 65%+ (iterate) | 70%+ |
| **Free --> Trial Start** | 5-10% | 8-12% | 10-15% | 12-18% |
| **Trial --> Paid** | -- | 30-40% | 35-45% | 40-50% |
| **Total Paid Users** | 0-3 | 10-25 | 30-80 | 100-300 |
| **MRR** | $0-30 | $100-250 | $300-800 | $1,000-3,000 |
| **WAL-3 (North Star)** | 15-30 | 50-100 | 150-350 | 500-1,500 |
| **App Store Rating** | N/A | 4.5+ (from beta testers) | 4.3+ | 4.3+ |
| **TikTok Followers** | 500-700 | 800-1,500 | 2,000-5,000 | 5,000-15,000 |

### When to Worry

| Signal | Threshold | Action |
|---|---|---|
| D1 retention below 25% | Below 25% after 100+ installs | Onboarding is broken. User is not reaching the aha moment. Redesign first session. |
| Onboarding completion below 40% | Below 40% | Too many steps, too much friction, or value prop unclear. Cut onboarding to 3 screens max. |
| Zero paid conversions after 500 downloads | 0 paid after 500 free | Paywall is either too aggressive (hitting before value) or too passive (users never see it). A/B test timing. |
| App Store rating below 3.5 | Below 3.5 after 10+ reviews | Read every review. Fix the top complaint. Respond publicly. |
| TikTok content getting <500 views consistently | <500 views after 20+ posts | Format isn't working. Test a completely different format. Consider face-to-camera vs. text-only. |

### Milestone Celebrations (Keep Yourself Motivated)

| Milestone | Target Date | Celebration |
|---|---|---|
| First download (not you or your mom) | Day 1 | Screenshot it. Frame it. Seriously. |
| First paid subscriber | Day 3-7 | Someone valued your work at $9.99/mo. That's real. |
| 100 downloads | Day 7-14 | Post about it. Building-in-public content. |
| 10 paying subscribers | Day 14-30 | ~$100/mo MRR. You have a business. |
| First organic 5-star review | Day 7-30 | Screenshot, save for marketing materials. |
| 1,000 downloads | Day 30-60 | You've found product-market fit signal. |
| $1,000 MRR | Day 60-120 | Across all apps, this is your "ramen profitable" moment. |

---

## 9. Pricing Validation

### Current Pricing

| App | Monthly | Assessment |
|---|---|---|
| IELTS Vocab | $9.99/mo | Under review |
| MedVocab | $14.99/mo | Under review |
| VocabX General | $9.99/mo | Under review |
| Lexicon | $9.99/mo | Under review |
| LegalLex | $14.99/mo | Under review |

### Competitive Pricing Landscape

| Competitor | Pricing | What You Get |
|---|---|---|
| Duolingo Super | $12.99/mo or $89.99/yr | Full language course (not vocab-specific) |
| Quizlet Plus | $35.99/yr (~$3/mo) | Flashcards (generic, not curated) |
| Magoosh IELTS | $99-149 one-time | Full IELTS prep (not vocab-specific) |
| Dean Vaughn Medical | $11.99/mo | Medical terminology (limited to 350 terms) |
| Picmonic | $12.99/mo or $77/yr (student) | Visual mnemonics (broader than terminology) |
| Anki | Free (iOS: $24.99 one-time) | DIY flashcards (no curation, no UX) |

### Pricing Recommendation

**IELTS Vocab: Launch at $6.99/mo, raise to $9.99 after 500 paid subscribers.**

Here's why:

1. **RevenueCat data shows lower-priced apps convert trial-to-paid at 47.8% vs. 28.4% for higher-priced.** At launch, you need conversions more than revenue per user. 100 users at $6.99 ($699 MRR) beats 50 users at $9.99 ($500 MRR).

2. **$6.99 is an impulse price for students.** IELTS test-takers are often students from developing countries (India, Pakistan, Philippines, Vietnam, Iran). $9.99 USD/mo is a real decision. $6.99 feels like "a coffee."

3. **You can always raise prices.** Early adopters lock in at $6.99. New users pay $9.99 later. Grandfather clause builds goodwill and reduces churn for your first cohort.

4. **Anchoring against alternatives:** $6.99/mo vs. $99+ for Magoosh, $155/yr for Picmonic, or $200+/hr for tutors. VocabX is the obvious value choice at any price under $10.

**Full pricing architecture:**

| Plan | Monthly | Annual | Savings |
|---|---|---|---|
| Free | $0 | $0 | -- |
| Premium Monthly | $6.99/mo (launch) --> $9.99/mo (post-500 subs) | -- | -- |
| Premium Annual | -- | $49.99/yr (launch) --> $79.99/yr | 40% vs. monthly |
| Early Bird (waitlist) | -- | $34.99/yr (first 100 only) | 58% vs. monthly |

**Annual plan strategy:**
- Only show the annual plan after the user's 3rd session (they need to see value first).
- Annual plan includes a 7-day free trial (monthly does not).
- At $49.99/yr, you're at $4.17/mo effective -- cheaper than Quizlet Plus and positioned as the best value in IELTS vocab prep.

**MedVocab/LegalLex at $14.99/mo: Keep it.**
- Professional/medical students have higher willingness to pay.
- Fewer alternatives exist.
- Anchor against Picmonic at $12.99/mo and Amboss at $24.99/mo.
- But offer a student discount: $9.99/mo with .edu email verification (or honor system).

**Lexicon at $9.99/mo: Consider $7.99/mo.**
- This is an identity/aesthetic purchase, not a professional tool.
- The audience is Gen Z with limited disposable income.
- $7.99 is the "streaming service" price point they're used to.

### Price Testing Plan (Post-Launch)

Use RevenueCat's A/B testing (built in) to test:
- **Test 1 (Month 2):** $6.99/mo vs. $9.99/mo for new users. Measure: trial starts, conversion rate, 30-day LTV.
- **Test 2 (Month 3):** Annual plan placement: show on paywall vs. show after 3rd session. Measure: annual vs. monthly split, total revenue.
- **Test 3 (Month 4):** Free trial length: 3-day vs. 7-day. Measure: trial-to-paid conversion.

---

# APPENDIX: Context File Updates

The following context files should be updated with VocabX data now that this analysis is complete.

---

## Updated: context/product.md

```markdown
## Product Overview
- **Product Name**: VocabX (platform); IELTS Vocab (first app)
- **Category**: Education / Vocabulary Learning
- **Platform**: iOS (React Native/Expo, multi-app from single codebase)
- **Tech Stack**: React Native, Expo, Supabase, RevenueCat, PostHog

## Problem & Solution
- **Core Problem**: Vocabulary learning apps are either too generic (Duolingo), too manual (Anki), or too expensive (Magoosh). No app combines curated niche vocabulary with modern spaced repetition and an engaging mobile-first UX.
- **Current Alternatives**: Duolingo (generic), Anki (powerful but ugly/manual), Quizlet (generic flashcards), Magoosh (expensive full-course), paper word lists
- **Our Solution**: TikTok-style word feed + FSRS spaced repetition + quiz games, specialized by niche (IELTS, Medical, Legal, Literary, General)
- **Key Differentiator**: Niche curation + FSRS algorithm + mobile-first UX. One codebase, 5 focused apps.

## Positioning
- **Market Category**: Vocabulary learning (subset of language learning / test prep)
- **Target Customer**: IELTS test-takers (first), medical students, law students, dark academia/literary enthusiasts, young professionals
- **Positioning Statement**: "For IELTS test-takers who need Band 7+ vocabulary, IELTS Vocab is the vocabulary app that uses spaced repetition to guarantee you remember every word -- not just for test day, but permanently."

## Features & Roadmap
- **Core Features**: TikTok-style word feed, FSRS spaced repetition, quiz games, streaks, achievements, iOS widget, push notifications, offline cache
- **Current Focus**: Launch IELTS Vocab as first app
- **What We're NOT Building**: Full IELTS prep course, grammar lessons, speaking practice, writing correction

## Business Model
- **Revenue Model**: Freemium subscription (free tier: 5 words/day, 5 reviews/day, 1 quiz/day)
- **Pricing**: $6.99-9.99/mo (general/IELTS), $14.99/mo (medical/legal)
- **Unit Economics**: Target LTV $30-60 (IELTS, 3-6 month lifecycle), CAC $0-5 (organic-first)
```

## Updated: context/metrics.md

```markdown
## North Star Metric
- **Metric**: WAL-3 (Weekly Active Learners who complete 3+ review sessions)
- **Current Value**: 0 (pre-launch)
- **Target**: 200 by Month 1, 500 by Month 2, 1,200 by Month 3
- **Why This Metric**: Leading indicator of retention, revenue, and referral. Users who review 3+/week hit free-tier limits and convert.

## Pirate Metrics (AARRR)
| Stage | Metric | Current | Target | Status |
|-------|--------|---------|--------|--------|
| Acquisition | App Store installs | 0 | 500-1,200/mo | Pre-launch |
| Activation | Onboarding completion rate | 0% | 60%+ | Pre-launch |
| Retention | D7 / D30 retention | 0% | 22% / 10% | Pre-launch |
| Revenue | Free-to-paid conversion | 0% | 8% of MAU | Pre-launch |
| Referral | K-factor | 0 | 0.15 | Pre-launch |
```

---

# Summary of Recommendations (Priority Order)

1. **Launch IELTS Vocab first.** Strongest market signal, built-in urgency (exam dates), proven willingness to pay, natural viral channel (WhatsApp study groups).

2. **Price at $6.99/mo for launch.** Optimize for conversion volume, not revenue per user. Raise to $9.99 after 500 paid subscribers.

3. **North Star = WAL-3.** Track weekly active learners with 3+ review sessions. Everything else is downstream.

4. **Invest 4 hours/week in TikTok content.** The "Do You Actually Know This Word?" format is your repeatable content play. 7 videos/week, batch-produced on Sunday.

5. **Build the anti-churn architecture before launch.** The Week 2 Intervention protocol (Section 3, Layer 3) is your single highest-ROI feature investment. Most education apps hemorrhage users at Day 8-14. Don't be most apps.

6. **Ship share cards at launch.** Beautiful, branded word cards with deep links are your primary growth loop. Low effort, high compounding returns.

7. **Streak Shields, not just streaks.** The anti-fragility mechanic (Section 6) is the difference between "users who quit after breaking a streak" and "users who recover and stay."

8. **Start Reddit participation today.** Not promotion -- genuine answers to IELTS vocabulary questions in r/IELTS. Build credibility for 2+ weeks before you ever mention your app.

---

*Analysis produced by Startup OS /growth + /launch workflows. Research-backed with 2025-2026 benchmark data.*

Sources:
- [Education App Benchmarks 2026 - Business of Apps](https://www.businessofapps.com/data/education-app-benchmarks/)
- [App Retention Benchmarks 2026 - Enable3](https://enable3.io/blog/app-retention-benchmarks-2025)
- [Mobile App Retention Benchmarks - UXCam](https://uxcam.com/blog/mobile-app-retention-benchmarks/)
- [State of Subscription Apps 2025 - RevenueCat](https://www.revenuecat.com/state-of-subscription-apps-2025/)
- [IELTS Practice and Exam Platform Market Analysis 2026](https://www.cognitivemarketresearch.com/ielts-practice-and-exam-platform-market-report)
- [IELTS Platform Market Size & Growth 2035](https://www.globalmarketstatistics.com/market-reports/ielts-practice-and-exam-platform-market-11616)
- [Best Medical Terminology Study App 2026](https://www.mindomax.com/best-medical-terminology-study-app-in-2026)
- [How Duolingo Reignited User Growth - Lenny's Newsletter](https://www.lennysnewsletter.com/p/how-duolingo-reignited-user-growth)
- [Duolingo Customer Retention Strategy 2026 - Propel](https://www.trypropel.ai/resources/duolingo-customer-retention-strategy)
- [Duolingo Gamification Secrets - Orizon](https://www.orizon.co/blog/duolingos-gamification-secrets)
- [ASO in 2026 - ASO Mobile](https://asomobile.net/en/blog/aso-in-2026-the-complete-guide-to-app-optimization/)
- [ASO Keyword Research 2026 - MobileAction](https://www.mobileaction.co/blog/aso-keyword-research/)
- [SaaS Freemium Conversion Rates 2026 - First Page Sage](https://firstpagesage.com/seo-blog/saas-freemium-conversion-rates/)
- [TikTok for Education 2026 - MegaDigital](https://megadigital.ai/en/blog/tiktok-for-education/)
- [TikTok Educational Trends 2026 - Hooked](https://www.tryhooked.ai/trends/tiktok/educational)
- [Indie App Marketing Strategies 2026 - Rapid App Store](https://rapidappstore.com/blog/indie-app-marketing-strategies)
- [How to Get Your First 100 Users 2026 - OpenHunts](https://openhunts.com/blog/how-to-get-your-first-100-users)
