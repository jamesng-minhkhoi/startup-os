# Competitive Analysis Workflow

Deep competitive analysis producing actionable intelligence: competitive brief, battlecards, positioning maps, and strategic response plan.

## Steps

1. **Load Context**: Read `context/market.md` and `context/product.md`. Check for existing competitive analysis in `outputs/strategy/`.

2. **Landscape Mapping** (skill: `competitive-brief`):
   - Identify competitors across 4 types: Direct, Indirect, Adjacent, Substitute.
   - Research via web: product pages, pricing, changelogs, reviews (G2, Capterra), job postings, social media.
   - Pull from Notion/Slack if connected and relevant.

3. **Deep Teardown** (skill: `competitive-brief`):
   - For each key competitor: company summary, product positioning, recent momentum.
   - Feature comparison matrix (detailed 5-level scale).
   - Pricing model analysis with hidden costs.
   - Win/loss analysis (if data available).

4. **Positioning Map** (skill: `obviously-awesome`, `blue-ocean-strategy`):
   - Build 2x2 positioning maps with meaningful axes.
   - Where are the gaps? Where is the blue ocean?
   - What are competitors' trade-offs? What are they deliberately NOT doing?

5. **Strategic Response** (skill: `competitive-brief`):
   - For each market trend: Lead, Fast Follow, Monitor, or Ignore?
   - What capabilities do we need to build vs. what's already differentiated?

6. **Battlecards** (skill: `competitive-battlecard`, `sales-enablement`):
   - Create per-competitor sales battlecards: their pitch, our counter, proof points.
   - Objection handling for common competitive objections.

7. **Output**: Save brief to `outputs/strategy/competitive-brief_{date}.md` and battlecards to `outputs/sales/`. Update `context/market.md`.

## Arguments

$ARGUMENTS — Which competitors to analyze, or a feature area to compare across competitors.
