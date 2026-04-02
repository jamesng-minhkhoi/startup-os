# Financial Review Workflow

Review financial health: statements, variance analysis, runway, and financial planning.

## Steps

1. **Load Context**: Read `context/metrics.md`. Check for existing financials in `outputs/finance/`.

2. **Financial Statements** (skill: `financial-statements`):
   - Review or create P&L, balance sheet, and cash flow statement.
   - Identify key ratios: gross margin, burn rate, runway, LTV/CAC.

3. **Variance Analysis** (skill: `variance-analysis`):
   - Actuals vs. plan for revenue, expenses, and cash.
   - For each significant variance: root cause and corrective action.
   - Flag trends that need attention before they become problems.

4. **Pricing Review** (skill: `pricing-strategy`):
   - Is pricing optimized? Apply the value metric test.
   - Check price-increase signals (conversion >40%, churn <3%, competitor pricing).
   - Good-Better-Best tier analysis.

5. **Revenue Operations** (skill: `revops`, `forecast`):
   - Review sales pipeline and forecast.
   - Revenue predictability: how reliable are projections?
   - Identify revenue concentration risks.

6. **Runway & Planning** (skill: `close-management`):
   - Current cash position and burn rate.
   - Months of runway remaining.
   - Scenarios: what extends/shortens runway?

7. **Output**: Save to `outputs/finance/financial-review_{date}.md`. Update `context/metrics.md`.

## Arguments

$ARGUMENTS — Paste financial data, describe current financial situation, or specify what to focus on (pricing, runway, variance, etc.).
