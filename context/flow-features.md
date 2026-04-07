# Flow & Features

> Source: PETIO - Product Overview.xlsx → Flow sheet
> Last updated: 2026-04-07

## Design Principles

- Always **fun & cute**
- Stand from the user's POV — what they're looking for and what they remember — then loop our product in

---

## 1. Onboarding

### Goal
- Collect pet's profile
- Introduce Peti and the app's core functions
- Use gamification so the user doesn't get bored

### Flow

**App Open → Peti Intro**
- Short intro popup, chat input visible

**Start Onboarding Game (Steps 2–9)**

| Step | Action | Data Collected |
|------|--------|----------------|
| 2 | Choose pet type (dog/cat) | Pet type |
| 3 | Customize appearance (avatar / color / style) | Avatar, Color |
| 4 | Select breed | Breed |
| 5 | Input name, select gender | Name, Gender |
| 6 | Pick birthday or age | Birthday / Age |
| 7 | Input weight and height | Weight, Height |
| 8 | Adopted? Microchip? (yes/no) | Adopted, Microchip |
| 9 | Medical conditions + optional notes | Medical Info, Note |

**Step 10 → Pet Summary Screen**
- Show full pet profile (avatar + all info)
- CTA: "Meet Peti"

**Step 11 → Memories Intro**
- Popup/card: "Capture and relive your pet's moments 🐾"
- Show sample or empty state
- CTA: Continue

**→ Enter Homepage**

### Design Notes
- Game must feel like progression, NOT a form
- Each step = 1 question only
- Use selection > typing whenever possible
- Allow skip for complex fields (medical, note)
- Total time target: 60–120s max
- Show progress (step indicator, progress bar, animation)
- Keep early steps super fast & fun — delay harder inputs visually
- Designer has freedom to rearrange sections for smoothness and to reduce screen count

---

## 2. AI Chatbox

### Goal
Help users get instant, personalized answers about their pet → build trust in Peti → drive repeated usage

### Entry Points
- Tap "Chat with Peti" banner on Homepage (includes suggested prompts — if tapped, skip straight to AI processing)
- Tap Peti icon on center bottom bar

### Response Formats

Peti responds in **two formats** depending on content complexity:

**Text** — for simple, straightforward information (e.g., quick answers, yes/no, short guidance)

**Widget/Card** — for complex, data-rich responses where readability matters:
- Product scan results (ingredients, safety rating, recommendation)
- Pet profile summaries
- Any response with structured data that benefits from visual layout

Widget goal: improve readability, support user behavior when consuming long or complex content.

### Flow

**Chat Intro**
- Greeting: "Hi Pawrent, what can I help you with today?"
- Suggested prompts:
  - What should my pet eat?
  - Is this food safe?
  - My pet is acting strange

**User Input Options**
- Type a question
- Tap a suggested prompt
- Tap Scan button (product barcode)
- Tap Upload / Scan Document

---

### Path A: Text Question

1. **AI Processing** — Read pet profile (age, breed, weight, allergies), detect intent (health / food / behavior)
2. **AI Response** — Return answer (text or widget), highlight key info, provide Do / Don't guidance

### Path B: Scan Product

1. **Scan** — Open camera, scan barcode or product
2. **AI Processing** — Identify product, analyze ingredients/type, cross-check with pet profile
3. **AI Response (Widget)** — Show evaluation: Safe / Caution / Unsafe, explain why, give recommendation

### Path C: Upload / Scan Document

1. **Upload** — Upload image or scan document (medical record, vaccine, etc.)
2. **AI Processing** — Extract key information, understand context (health / vaccine / note)
3. **AI Response** — Summarize key info, highlight important points, suggest actions:
   - Save to pet profile
   - Ask follow-up

---

### After Any Response
- **Follow-up suggestions** — Ask more questions, get deeper advice, save/track information
- **Continue or Exit** — Keep chatting or return to Homepage
