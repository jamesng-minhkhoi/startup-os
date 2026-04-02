# Sprint Planning Workflow

Plan a development sprint with prioritization, capacity planning, and clear deliverables.

## Steps

1. **Load Context**: Read `context/product.md` and `context/metrics.md`. Check existing roadmap in `outputs/product/`.

2. **Backlog Prioritization** (skill: `prioritize-features`, `product-management`):
   - Apply kill-criteria-first: define what would make us stop each initiative.
   - Score backlog using RICE (Reach, Impact, Confidence, Effort) or ICE (Impact, Confidence, Ease).
   - Apply the Bridge Migration Pattern for any feature replacements.

3. **Sprint Scope** (skill: `sprint-planning`, `roadmap-update`):
   - What's the sprint goal? (One sentence, tied to a quarterly rock.)
   - Apply capacity planning: 70% planned work, 20% tech debt, 10% exploration.
   - Don't solve capacity problems by pretending people can do more — solve by cutting scope.
   - Define what's IN and what's OUT.

4. **Spec Writing** (skill: `write-spec`):
   - For each major item, write a lightweight spec: problem, solution, success criteria, edge cases.
   - Include acceptance criteria that are testable.

5. **Dependencies & Risks** (skill: `risk-assessment`):
   - Map dependencies between items and with other teams/services.
   - Identify risks and mitigations.
   - Can we build simpler versions that avoid dependencies?

6. **Output**: Save to `outputs/product/sprint-plan_{date}.md`.

## Arguments

$ARGUMENTS — Sprint duration, team size, any fixed commitments or deadlines.
