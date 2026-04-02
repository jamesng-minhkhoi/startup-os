# Canvas Workshop

Generate or update a strategic canvas for your business. Supports Startup Canvas (recommended), Lean Canvas, and Business Model Canvas.

## Steps

1. **Load Context**: Read all context files. A canvas needs the full picture.

2. **Canvas Selection**:
   - **Startup Canvas** (skill: `startup-canvas`) — Recommended for startups. Includes defensibility test, trade-offs, North Star metric. Use when you need strategic depth.
   - **Lean Canvas** (skill: `lean-canvas`) — Use when you need speed over completeness, or when stakeholders expect this format.
   - **Business Model Canvas** (skill: `business-model`) — Use for established products or when presenting to traditional investors/advisors.

3. **Canvas Generation** (chosen skill):
   - Walk through each section with probing questions.
   - Challenge weak entries. Push for specificity.
   - Cross-reference sections for consistency.
   - For Startup Canvas: apply the Can't/Won't defensibility test.

4. **Validation Check** (skill: `lean-startup`):
   - For each section, identify the riskiest assumption.
   - What evidence do we have? What's Validation Ladder level?
   - Design experiments for top 3 unvalidated assumptions.

5. **Market Context** (skill: `blue-ocean-strategy`, `crossing-the-chasm`):
   - Overlay the canvas with market strategy: red ocean vs. blue ocean?
   - Where on the adoption lifecycle? Who's the beachhead?

6. **Output**: Save to `outputs/strategy/{canvas-type}_{date}.md`. Update `context/product.md` and `context/market.md`.

## Arguments

$ARGUMENTS — Which canvas type (startup/lean/bmc), or describe what you're trying to figure out and I'll recommend the right one.
