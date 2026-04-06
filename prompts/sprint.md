# Sprint Planning Workflow

Paste this into Claude Desktop to plan a sprint.

---

**Prompt:**

> Plan our next sprint. [SPRINT DURATION, TEAM SIZE, FIXED COMMITMENTS/DEADLINES]
>
> Follow these steps in order:
>
> 1. Read `context/product.md` and `context/metrics.md`. Check `outputs/product/` for existing roadmap
> 2. Use `prioritize-features` and `product-management` — apply kill-criteria-first, score backlog using RICE or ICE
> 3. Use `sprint-planning` and `roadmap-update` — define sprint goal (one sentence, tied to a quarterly rock), apply capacity: 70% planned / 20% tech debt / 10% exploration, define what's IN and OUT
> 4. Use `write-spec` — for each major item, write a lightweight spec with problem, solution, success criteria, and testable acceptance criteria
> 5. Use `risk-assessment` — map dependencies, identify risks and mitigations, simplify where possible to avoid dependencies
> 6. Save to `outputs/product/sprint-plan_2026-04-06.md`
