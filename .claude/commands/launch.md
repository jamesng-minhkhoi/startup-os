# Launch Planning Workflow

Plan a product launch across marketing, product, and operations. Chains launch strategy, campaign planning, content creation, and CRO.

## Steps

1. **Load Context**: Read `context/product.md` and `context/market.md`. Check for existing positioning in `outputs/strategy/`.

2. **Launch Strategy** (skill: `launch-strategy`):
   - Determine launch type: new product, major update, feature launch, or beta.
   - Apply the Five-Phase model: Internal → Alpha → Beta → Early Access → Full Launch.
   - Map channels using ORB framework (Owned / Rented / Borrowed).
   - Build the launch checklist (pre-launch, launch day, post-launch).

3. **Campaign Plan** (skill: `campaign-plan`, `marketing-ideas`):
   - Define campaign goals, audience, and timeline.
   - Select 3-5 marketing ideas from the 139-idea catalog filtered by stage and budget.
   - Plan the content calendar.

4. **Content & Copy** (skill: `copywriting`, `email-sequence`, `social-content`):
   - Write landing page copy (headline, subheadline, CTA, social proof, objections).
   - Design the email sequence (announcement, value, social proof, urgency, last chance).
   - Create social content for launch day and surrounding days.

5. **Conversion Optimization** (skill: `signup-flow-cro`, `page-cro`, `onboarding-cro`):
   - Audit the signup flow for friction.
   - Review landing page for CRO best practices.
   - Plan the onboarding experience for new users.

6. **Operations Checklist** (skill: `runbook`, `risk-assessment`):
   - Create the launch day runbook (who does what, when).
   - Identify risks and mitigation plans (site goes down, negative feedback, etc.).

7. **Output**: Save to `outputs/marketing/launch-plan_{date}.md`. Save copy assets separately.

## Arguments

$ARGUMENTS — What you're launching, when, and any constraints (budget, timeline, team size).
