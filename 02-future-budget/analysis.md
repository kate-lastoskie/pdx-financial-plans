# Future Budget: Cost of Raising Two Children (2-Year Gap) and Baseline Living Expenses

**Supersession note:** This document supersedes Sections 3 (Childcare Costs), 4 (Children's Health Insurance Premium), and 5 (Baseline Living Expenses) of `03-home-affordability/analysis.md`. That document is being updated separately to reference this file as the source for those figures rather than containing the content directly. The child-count-and-phase structure (2-year age gap, correctly modeled so the two children are never simultaneously in infant care) carries over from that draft, but this version adds an inflation dimension the prior draft did not have, and is the version of record going forward.

Prepared for Kate and Lucas. Scope: what raising two children, born 2 years apart, actually costs in the dollars of the year each cost is incurred, plus how baseline (non-housing, non-childcare) household living expenses scale with child count. This is an input document; `03-home-affordability/analysis.md` should cite specific figures from Section 7 rather than re-deriving them. All arithmetic (compound inflation projections, cumulative totals) was computed in a Python script and cross-checked before being placed in these tables.

Inputs taken as given from `shared/assumptions.md`: two children planned, cost inputs to be researched against current Multnomah County / Portland-area data rather than assumed.

---

## 1. Timeline and Method Overview

- **Birth years are not specified in `shared/assumptions.md`.** This document assumes, as a stated modeling choice: **Child A born 2027, Child B born 2029** (a 2-year gap, starting next year from the current date of this analysis, July 2026). If the household's actual timeline differs, every phase below shifts by the same number of years but the today's-dollars figures and the per-year inflation factors (Section 5) remain usable; only the calendar-year labels would need to change.
- Per known-modeling-issues.md (issue 2), a 2-year gap means Child A is already in the preschool-age range by the time Child B is born as an infant. The two children are never simultaneously in infant care. Peak overlap is one infant plus one preschooler.
- Five phases are used throughout this document, defined by Child A's age (Child B's age and status follow automatically from the 2-year gap):

| Phase | Child A age | Child B age | Calendar years (assumed) | Description |
|---|---|---|---|---|
| 1 | 0-1 | not yet born | 2027-2028 | Child A infant only |
| 2 | 2-3 | 0-1 | 2029-2030 | Peak overlap: Child A preschool, Child B infant |
| 3 | 4 | 2 | 2031 | Both preschool |
| 4 | 5-6 | 3-4 | 2032-2033 | Child A school-age aftercare, Child B preschool |
| 5 | 7-11 | 5-9 | 2034-2038 | Both school-age, through Child A turning 12 |

- The modeled window (Section 6) runs 2027 through 2038, 12 calendar years, ending when Child A turns 12 (early 2039), consistent with the 12-year cumulative window used in the prior draft's childcare calculation.

---

## 2. Childcare Costs by Phase

### Method

- Center-based daycare rates, Multnomah County / Portland, 2026 dollars:
  - Infant care: **$1,750/month** (daycarecostguide.com and childcarecost.org 2026 city/county data, placing Multnomah County infant center care around $1,763/month and central Portland neighborhoods in a $1,600-$2,200/month range).
  - Preschool (age ~2-5): **$1,200/month** (daycarecalc.com / daycarecostguide.com 2026, reporting a $1,170-$1,600/month range for Portland preschool care).
  - School-age after-care (age 5+): **$750/month** (daycarecalc.com "After-School Care Cost 2026" and nannylane.com Portland data, reporting a $500-$980/month range depending on program type; $750 used as a mid-range point estimate).
- These figures are **daycare-center prices**, stated explicitly as such per issue #17. Alternative arrangements cost meaningfully more:
  - Nanny share: roughly **$350-$600/week per family** (about $1,500-$2,600/month) (care.com and nannylane.com Portland data, 2026).
  - Private full-time nanny: roughly **$930/week** (about $4,000/month) (care.com and nannylane.com Portland data, 2026).
  - Neither alternative is carried through the phase and inflation tables below; both are materially more expensive than center-based care at the low end and substantially more at the high end, and would inflate at the same childcare-specific rate assumed in Section 5 if projected forward.
- Multnomah County's "Preschool for All" program offers free preschool for eligible 3- and 4-year-olds and could reduce the preschool-phase figure for a qualifying family. This is not built into the $1,200/month figure, which reflects private-pay center care; it is noted as a factor that could lower Phase 2-4 costs for a household that qualifies and enrolls.

### Cost by Phase, Two Children (2026 dollars, center-based care)

| Phase | Child A | Child B | Monthly childcare cost (2026 $) |
|---|---|---|---|
| 1: Years 0-2 | Infant | (not yet born) | $1,750 |
| 2: Years 2-4 | Preschool | Infant | **$2,950 (peak overlap)** |
| 3: Years 4-5 | Preschool | Preschool | $2,400 |
| 4: Years 5-7 | School-age after-care | Preschool | $1,950 |
| 5: Years 7-12 | School-age after-care | School-age after-care | $1,500 |

### Cost by Phase, One Child (2026 dollars, for reference)

| Phase | Monthly childcare cost (2026 $) |
|---|---|
| Infant (0-2) | $1,750 |
| Preschool (2-5) | $1,200 |
| School-age after-care (5+) | $750 |

Cumulative check, today's dollars, not just peak-month comparison (per issue #18): summing monthly cost across each phase from Child A's birth through Child A turning 12 (the 12-year window in Section 1) gives **$278,400** in total childcare spend for two children under this 2-year-gap structure, in 2026 dollars, before any inflation adjustment. Section 6 restates this same total in nominal (inflated) dollars.

---

## 3. Children's Health Insurance Premium

### Method

- The KFF 2025 Employer Health Benefits Survey (KFF, 2025) reports an average annual family-coverage premium of $26,993, of which employees contribute an average of $6,850/year ($571/month) for full family coverage (employee + spouse + children combined).
- The incremental cost of adding children specifically (as opposed to a spouse) varies by employer plan design; industry cost breakdowns (eHealth, moneygeek.com 2026 summaries) suggest the child-specific increment is commonly in a $200-$425/month range for one or two children combined.
- This document uses **$250/month for one child** and **$350/month for two children** as a stated point estimate within the cited range. Note that KFF's own survey series shows employer family-premium growth has historically outpaced general CPI (see Section 5); the general-inflation rate applied to this line item in Section 6 is therefore a conservative (likely lower-bound) projection for this specific cost.

| Number of children | Monthly premium (2026 $) |
|---|---|
| 1 | $250 |
| 2 | $350 |

---

## 4. Baseline Household Living Expenses

### Method

- Baseline living expenses cover groceries, transportation (fuel/insurance/maintenance, not a car payment), phone, subscriptions, personal care, and general household spending. They explicitly exclude rent/mortgage and childcare, which are modeled separately.
- No single authoritative "Portland household baseline spending" source was found within the scope of this analysis; this is a **reasoned build-up estimate**, stated explicitly as such:
  - Groceries: ~$900/month (two adults)
  - Transportation (fuel, insurance, upkeep, no car payment): ~$500/month
  - Phone/subscriptions/utility-adjacent services: ~$250/month
  - Personal care, clothing, incidental/miscellaneous household spending: ~$1,350/month
  - **Total, 0 children: ~$3,000/month**
- Per issue #13, baseline costs scale upward with child count (food, clothing, activities) rather than staying flat:
  - 1 child: **$3,300/month** (+10%, +$300/month attributable to the child)
  - 2 children: **$3,600/month** (+20%, +$600/month attributable to the children)

| Household composition | Baseline monthly living expenses (2026 $) | Increase attributable to children |
|---|---|---|
| 0 children | $3,000 | n/a |
| 1 child | $3,300 | +$300 |
| 2 children | $3,600 | +$600 |

Only the **increase attributable to children** (the $300 or $600 increment, not the full $3,000-$3,600 baseline) is carried into the child-cost totals in Sections 6 and 7, since the $3,000 base applies to the household regardless of child count and is not a child-rearing cost.

---

## 5. Inflation Assumptions

### General inflation (applies to health insurance premium and baseline living expenses)

- BLS CPI-U (Consumer Price Index for All Urban Consumers), 12-month change, June 2026: **3.5%**, down from 4.2% in May 2026 (BLS CPI news release, June 2026 results, reported July 14, 2026). Core CPI (excluding food and energy), 12-month change: **2.6%**.
- The Federal Reserve's longer-run inflation objective is **2%**, measured on the PCE price index (Federal Reserve FOMC Statement on Longer-Run Goals and Monetary Policy Strategy).
- **Stated assumption: 3.0%/year**, compounded annually, applied to health insurance premiums and baseline living expenses. This is a planning midpoint between the Fed's 2% long-run target and the more recent actual CPI reading of 3.5%, not a forecast of either series; it is a modeling choice, stated explicitly as such.

### Childcare-specific inflation (applies to childcare costs only)

- This repository's own `04-2001-vs-2026-comparison/analysis.md` found that childcare costs for a comparable arrangement (one infant plus one preschooler, center-based) grew approximately 47% more than general CPI inflation over the 25 years from 2001 to 2026, roughly **1.5 percentage points per year above CPI** (internal analysis, based on estimated 2001 figures and sourced 2026 figures; the 2001 baseline in that analysis is a labeled estimate, not a confirmed figure, so the 47%/1.5pp figure should be treated as directional).
- Independent current sourcing corroborates a similar multiplier: Axios ("Cost of child care rising faster than inflation," May 2025) reports childcare costs rising **1.5 times faster than overall inflation**, up 5.2% year-over-year as of September 2025; The Hill ("Child care cost rising at nearly twice the pace of inflation," 2025) reports similar magnitude; Bank of America Institute ("The many costs of childcare," October 2025) documents childcare costs growing faster than headline CPI over multiple years.
- **Stated assumption: 4.5%/year**, compounded annually, applied to childcare costs. This equals the 3.0% general-inflation assumption plus 1.5 percentage points (consistent with the internal analysis's framing) and is also consistent with the ~1.5x-general-inflation framing reported by Axios. This is a stated modeling assumption, not a precise forecast, and is treated separately from the general inflation rate throughout Section 6.

| Cost category | Annual inflation assumption | Basis |
|---|---|---|
| Childcare | 4.5% | General inflation (3.0%) + 1.5 percentage points, per historical childcare-vs-CPI excess (internal and external sources) |
| Health insurance premium | 3.0% | General inflation assumption (see caveat in Section 3 that premiums have historically grown faster) |
| Baseline living expenses | 3.0% | General inflation assumption |

---

## 6. Inflation-Projected Costs by Phase

### Method

- Base year for all "today's dollars" figures: **2026**.
- For each phase, the nominal (inflated) monthly cost is shown at the **start year** and the **end year** of that phase, since inflation continues to compound within a multi-year phase. Inflation factor = (1 + annual rate) ^ (calendar year minus 2026), applied separately at the childcare rate (4.5%) and the general rate (3.0%, applied to health premium and the baseline-living increase attributable to children).
- All calculations were run in Python; see the per-year table below for the full year-by-year detail underlying the phase-start/phase-end figures.

### Childcare, Health Premium, and Baseline-Increase by Phase: Today's Dollars vs. Nominal Dollars

| Phase | Calendar years | Childcare (2026 $) | Health premium (2026 $) | Baseline increase (2026 $) | **Total, today's $/mo** | Childcare, nominal @ start | Health premium, nominal @ start | Baseline increase, nominal @ start | **Total, nominal $/mo @ start of phase** | **Total, nominal $/mo @ end of phase** |
|---|---|---|---|---|---|---|---|---|---|---|
| 1: Years 0-2 (Child A infant only) | 2027-2028 | $1,750 | $250 | $300 | **$2,300** | $1,829 | $258 | $309 | **$2,395** | **$2,495** |
| 2: Years 2-4 (peak overlap) | 2029-2030 | $2,950 | $350 | $600 | **$3,900** | $3,366 | $382 | $656 | **$4,405** | **$4,587** |
| 3: Years 4-5 (both preschool) | 2031 | $2,400 | $350 | $600 | **$3,350** | $2,991 | $406 | $696 | **$4,092** | **$4,092** (single-year phase) |
| 4: Years 5-7 (school-age + preschool) | 2032-2033 | $1,950 | $350 | $600 | **$2,900** | $2,539 | $418 | $716 | **$3,674** | **$3,822** |
| 5: Years 7-12 (both school-age) | 2034-2038 | $1,500 | $350 | $600 | **$2,450** | $2,133 | $443 | $760 | **$3,337** | **$3,898** |

### Year-by-Year Detail (Total Monthly Cost: Childcare + Health Premium + Baseline Increase)

| Calendar year | Phase | Today's $ (2026), monthly | Nominal $, monthly |
|---|---|---|---|
| 2027 | 1 | $2,300 | $2,395 |
| 2028 | 1 | $2,300 | $2,495 |
| 2029 | 2 | $3,900 | $4,405 |
| 2030 | 2 | $3,900 | $4,587 |
| 2031 | 3 | $3,350 | $4,092 |
| 2032 | 4 | $2,900 | $3,674 |
| 2033 | 4 | $2,900 | $3,822 |
| 2034 | 5 | $2,450 | $3,337 |
| 2035 | 5 | $2,450 | $3,469 |
| 2036 | 5 | $2,450 | $3,606 |
| 2037 | 5 | $2,450 | $3,749 |
| 2038 | 5 | $2,450 | $3,898 |

### Cumulative Total, 2027-2038 (12-Year Window, Child A Age 0 Through Turning 12)

- Method: annual cost = monthly total x 12 for each calendar year, summed across the 12-year window. The today's-dollars total uses the flat 2026 monthly figure for every year in a given phase (no inflation). The nominal total uses each individual year's own inflation-adjusted monthly figure before annualizing.

| Cost category | Cumulative, today's (2026) dollars | Cumulative, nominal (inflated) dollars |
|---|---|---|
| Childcare | $278,400 | $365,735 |
| Children's health insurance premium | $48,000 | $58,886 |
| Baseline living increase attributable to children | $79,200 | $97,721 |
| **Total** | **$405,600** | **$522,342** |

The nominal cumulative total ($522,342) is about 28.8% higher than the same costs expressed in today's (2026) dollars ($405,600), reflecting the compounding effect of the 3.0%/4.5% inflation assumptions over a 12-year window. This is the effect of the stated inflation assumptions, not an independent forecast; if actual future inflation runs above or below the assumed rates, the nominal figure would change accordingly while the today's-dollars figure would not.

---

## 7. Monthly Child-Attributable Cost by Phase (Primary Reference Table)

This table is the primary reference point for `03-home-affordability/analysis.md`. It gives, for each phase, the combined monthly cost of childcare, children's health insurance premium, and the baseline-living increase attributable to children, in both today's (2026) dollars and inflation-projected nominal dollars (evaluated at the start of each phase, per Section 6).

| Phase | Calendar years | Childcare | Health premium | Baseline increase (children) | **Total, today's $/mo (2026)** | **Total, nominal $/mo (start of phase)** |
|---|---|---|---|---|---|---|
| 1: Infant only (Child A) | 2027-2028 | $1,750 | $250 | $300 | **$2,300** | **$2,395** |
| 2: Peak overlap (infant + preschool) | 2029-2030 | $2,950 | $350 | $600 | **$3,900** | **$4,405** |
| 3: Both preschool | 2031 | $2,400 | $350 | $600 | **$3,350** | **$4,092** |
| 4: School-age + preschool | 2032-2033 | $1,950 | $350 | $600 | **$2,900** | **$3,674** |
| 5: Both school-age | 2034-2038 | $1,500 | $350 | $600 | **$2,450** | **$3,337** |

- Peak overlap phase (Phase 2, 2029-2030) is the highest-cost phase on both a today's-dollars and a nominal-dollars basis. Today's dollars: $3,900/month. Nominal dollars, in the year it begins (2029): $4,405/month. By the end of that phase (2030): $4,587/month.
- Across the full 12-year window (2027-2038), the cumulative child-attributable cost (childcare + health premium + baseline increase) totals $405,600 in today's dollars and $522,342 in nominal (inflation-projected) dollars (Section 6).
- All figures in this table exclude housing/mortgage costs, the Seattle condo carrying cost, and adult-only baseline living expenses (the $3,000/month floor from Section 4), which are addressed in `03-home-affordability/analysis.md`.

---

## Sources

- daycarecostguide.com and childcarecost.org, Multnomah County / Portland infant and preschool daycare rates, 2026
- daycarecalc.com, "After-School Care Cost 2026" and Portland-area daycare cost data
- nannylane.com, Portland, OR nanny and nanny-share cost data, 2026
- care.com, Portland, OR nanny cost data, 2026
- Multnomah County "Preschool for All" program (noted qualitatively, not quantified into the $1,200/month figure)
- KFF (Kaiser Family Foundation), 2025 Employer Health Benefits Survey: https://www.kff.org/health-costs/2025-employer-health-benefits-survey/
- eHealth and moneygeek.com, 2026 summaries of employer health plan child-dependent cost increments
- U.S. Bureau of Labor Statistics, CPI news release, June 2026 results (12-month CPI-U change 3.5%, core CPI 2.6%), published July 14, 2026: https://www.bls.gov/news.release/cpi.nr0.htm
- CNBC, "Here's the inflation breakdown for June 2026, in one chart," July 14, 2026: https://www.cnbc.com/2026/07/14/inflation-cpi-june-2026-in-one-chart.html
- Federal Reserve, "Statement on Longer-Run Goals and Monetary Policy Strategy" (2% PCE inflation objective)
- This repository, `04-2001-vs-2026-comparison/analysis.md`, Section 4 (childcare cost comparison, internal analysis of ~47% excess growth over CPI, 2001-2026)
- Axios, "Cost of child care rising faster than inflation," May 24, 2025: https://www.axios.com/2025/05/24/child-care-costs
- The Hill, "Child care cost rising at nearly twice the pace of inflation, research says," 2025: https://thehill.com/policy/healthcare/4696778-child-care-cost-inflation-women-in-workforce/
- Bank of America Institute, "The many costs of childcare," October 28, 2025: https://institute.bankofamerica.com/content/dam/economic-insights/childcare-costs.pdf

## Method Notes Addressed From Known Modeling Issues

This document was built to independently avoid the relevant issues in `shared/known-modeling-issues.md`: the 2-year age gap is modeled as one infant plus one preschooler at peak, never two infants simultaneously (issue 2); children's health insurance premium is included as an explicit, separate line item (issue 6); baseline living expenses scale with child count rather than staying flat, and only the child-attributable increment is carried into child-cost totals (issue 13); childcare cost is labeled as center-based, with nanny/nanny-share ranges given as a materially more expensive, explicitly labeled alternative (issue 17); a cumulative (not just peak-month) cost figure is shown, in both today's and nominal dollars, so that timing/gap comparisons are not based on peak cost alone (issue 18); external cost and inflation estimates are checked against current, cited sources and labeled as assumptions where a precise figure was not available (issue 19); prose throughout states figures and mechanics neutrally, without persuasive or advice-toned framing (issue 20).
