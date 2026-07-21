# Portland Financial Planning

Financial planning exercises for Kate & Lucas, done with Claude.

## Exercises

1. **`01-current-budget/`** - Current-day budget, saving for a house in Portland and a wedding.
2. **`02-future-budget/`** - Cost of raising two children (spaced 2 years apart): childcare, children's health insurance, and general child-related living cost increases, projected forward with inflation. Feeds into `03` and `06`.
3. **`03-home-affordability/`** - Home-purchase cost mechanics only: after-tax income by scenario, all-in monthly housing cost by price point, closing costs, mortgage rate sensitivity. Does not include child costs. Feeds into `06`.
4. **`04-2001-vs-2026-comparison/`** - Buying a home in 2001 (parents) vs. 2026 (us).
5. **`05-seattle-condo-decision/`** - Keep or sell the existing Seattle condo.
6. **`06-affordability-assessment/`** - Combines `02` (child costs) and `03` (home costs) as inputs and tests standard home affordability rules of thumb (28/36 rule, 25%-of-net-income rule, price-to-income multiplier) against the full cash-flow picture, including the Seattle condo carrying cost.

## Shared

`shared/` holds inputs and assumptions common across exercises (income, savings, debts, rates) so each exercise isn't recomputing them from scratch, plus a running list of modeling issues to avoid repeating.

## Status

`01` through `06` have content. Each folder's `README.md` is the report itself (not a pointer to a separate file), so it renders automatically when browsing that folder on GitHub. Each analysis document states its sources and which upstream documents it pulls numbers from.
