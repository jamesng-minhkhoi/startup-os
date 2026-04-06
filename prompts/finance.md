# Financial Review Workflow

Paste this into Claude Desktop to review financial health.

---

**Prompt:**

> Run a financial review for Petio. [PASTE FINANCIAL DATA OR DESCRIBE SITUATION — focus on: pricing / runway / variance / all]
>
> Follow these steps in order:
>
> 1. Read `context/metrics.md`. Check `outputs/finance/` for existing financials
> 2. Use `financial-statements` — review or create P&L, balance sheet, cash flow. Key ratios: gross margin, burn rate, runway, LTV/CAC
> 3. Use `variance-analysis` — actuals vs plan for revenue, expenses, cash. Root cause and corrective action for each significant variance
> 4. Use `pricing-strategy` — is pricing optimized? Apply value metric test, check price-increase signals, Good-Better-Best tier analysis
> 5. Use `revops` and `forecast` — pipeline review, revenue predictability, concentration risks
> 6. Runway & planning: current cash, burn rate, months remaining, scenarios that extend/shorten
> 7. Save to `outputs/finance/financial-review_2026-04-06.md` and update `context/metrics.md`
