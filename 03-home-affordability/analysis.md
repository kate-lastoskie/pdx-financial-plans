# Home Affordability Analysis: Portland, OR

**Note on document scope (restructuring, July 2026):** This document covers home-purchase cost mechanics only: after-tax household income by scenario, all-in monthly housing cost by price point, closing costs, and mortgage-rate sensitivity on housing cost itself. Child-rearing costs (childcare, children's health insurance premium, and baseline living expense scaling by child count) are modeled separately in `02-future-budget/analysis.md`. The combined affordability verdict, the combined monthly cash flow view, and emergency fund runway under income-loss scenarios are addressed in `06-affordability-assessment/analysis.md`, which combines the home-cost figures here with the child-cost figures from `02-future-budget/analysis.md` and applies standard affordability rules of thumb.

Prepared for Kate and Lucas. Covers after-tax income under multiple employment scenarios, all-in monthly housing cost at five price points, closing costs, and mortgage-rate sensitivity on housing cost. All dollar figures are nominal (2026 dollars), monthly unless stated otherwise. All arithmetic was computed in a Python script and checked against hand-verified sample calculations before being placed in these tables (see Method notes under each section).

This document supersedes an earlier draft that contained calculation errors and persuasive framing (see `shared/known-modeling-issues.md`). Figures here are independently derived and cited; no numbers were carried forward from the earlier draft.

Inputs taken as given from `shared/assumptions.md`: Kate $165,000/yr gross, Lucas $143,520/yr gross, Married Filing Jointly, $200,000 actual down payment (not a 20% assumption), $70,000 emergency fund held separately from the down payment.

---

## 1. After-Tax Monthly Income by Scenario

### Method

- Federal tax: 2026 Married Filing Jointly brackets and standard deduction ($32,200), per IRS Revenue Procedure 2025-32 as reported by the Tax Foundation (accessed July 2026).
- Oregon tax: 2026 Married Filing Jointly brackets and standard deduction ($5,820), per Oregon Department of Revenue, *Oregon Withholding Tax Formulas* (Publication 150-206-436, effective January 1, 2026).
  - **Simplification stated explicitly:** this model does not apply Oregon's federal-tax subtraction (a below-the-line adjustment for federal tax paid). Per the same DOR publication, that subtraction phases out entirely for a married household with combined wages at or above $290,000, which covers the two-income scenario (combined gross $308,520). It would apply partially in the single-income scenarios below, so Oregon tax in those rows is a slight overestimate (on the order of a few hundred dollars a year), not an underestimate.
- FICA: Social Security at 6.2% applied separately to each spouse's own wages up to the 2026 wage base of $184,500 per person (Social Security Administration, 2026 wage base); Medicare at 1.45% on all wages, no cap; Additional Medicare Tax of 0.9% on combined household Medicare wages above the $250,000 Married Filing Jointly threshold (IRS Topic No. 751, 2026 parameters).
  - **Modeling correction versus the prior draft:** traditional pre-tax 401(k) contributions reduce federal and Oregon taxable wages but do **not** reduce Social Security or Medicare wages. This model applies FICA to gross wages before any 401(k) deferral, which is the correct treatment.
- Retirement contributions modeled at three levels, applied per working spouse (pre-tax traditional 401(k)):
  - **Max**: $24,500/year per person, the 2026 IRS elective deferral limit (IRS, "401(k) limit increases to $24,500 for 2026," 2026). In any scenario with only one earner, "max" reflects only that one person's ability to contribute (never an invented combined figure).
  - **Partial**: 6% of gross salary per working spouse (a stated modeling assumption, not a researched figure).
  - **Minimal**: 3% of gross salary per working spouse (stated as representative of a common "match-only" contribution rate).
- Scenario (d), "both parents shift to lower-paying jobs," requires a defined resulting income, not an invented floor. This model uses an explicit, labeled assumption: **a 30% reduction from each person's current salary**, intended only as an illustrative placeholder for "a lower-hours or lower-responsibility role," not a researched labor-market figure. Kate's modeled lower salary: $115,500/yr. Lucas's modeled lower salary: $100,464/yr. The scenario is split into a **transition period** (one income drops before the other) and a **settled state** (both reduced), per the modeling requirement that a simultaneous instant change is unrealistic.

### 2026 Tax Bracket Reference

| Federal (MFJ) | Rate | Oregon (MFJ) | Rate |
|---|---|---|---|
| $0 - $24,800 | 10% | $0 - $9,100 | 4.75% |
| $24,800 - $100,800 | 12% | $9,100 - $22,800 | 6.75% |
| $100,800 - $211,400 | 22% | $22,800 - $250,000 | 8.75% |
| $211,400 - $403,550 | 24% | above $250,000 | 9.9% |
| $403,550 - $512,450 | 32% | | |
| $512,450 - $768,700 | 35% | | |
| above $768,700 | 37% | | |

Federal standard deduction (MFJ): $32,200. Oregon standard deduction (MFJ): $5,820. Social Security wage base (2026, per person): $184,500. Additional Medicare Tax threshold (MFJ, combined): $250,000.

### After-Tax Monthly Income by Scenario and Retirement Level

| Income scenario | Gross annual (combined) | Retirement level | Federal tax | Oregon tax | FICA (total) | Net monthly take-home |
|---|---|---|---|---|---|---|
| (a) Both working, current salaries | $308,520 | Max ($24.5K each) | $39,753 | $21,603 | $24,128 | $14,503 |
| (a) Both working, current salaries | $308,520 | Partial (6% each) | $47,070 | $24,622 | $24,128 | $16,182 |
| (a) Both working, current salaries | $308,520 | Minimal (3% each) | $49,291 | $25,538 | $24,128 | $16,692 |
| (b) Kate's income lost, Lucas only | $143,520 | Max ($24.5K) | $9,922 | $9,267 | $10,979 | $7,404 |
| (b) Kate's income lost, Lucas only | $143,520 | Partial (6%) | $12,020 | $10,657 | $10,979 | $8,438 |
| (b) Kate's income lost, Lucas only | $143,520 | Minimal (3%) | $12,967 | $11,034 | $10,979 | $8,686 |
| (c) Lucas's income lost, Kate only | $165,000 | Max ($24.5K) | $13,250 | $11,146 | $12,622 | $8,623 |
| (c) Lucas's income lost, Kate only | $165,000 | Partial (6%) | $16,462 | $12,424 | $12,622 | $9,466 |
| (c) Lucas's income lost, Kate only | $165,000 | Minimal (3%) | $17,551 | $12,857 | $12,622 | $9,752 |
| (d1) Transition: Kate reduced, Lucas still current | $259,020 | Max | $28,544 | $17,230 | $19,896 | $12,029 |
| (d1) Transition: Kate reduced, Lucas still current | $259,020 | Partial | $35,905 | $20,157 | $19,896 | $13,960 |
| (d1) Transition: Kate reduced, Lucas still current | $259,020 | Minimal | $37,768 | $20,837 | $19,896 | $14,396 |
| (d2) Settled: both at reduced salaries | $215,964 | Max | $19,072 | $13,462 | $16,521 | $9,826 |
| (d2) Settled: both at reduced salaries | $215,964 | Partial | $27,001 | $16,616 | $16,521 | $11,906 |
| (d2) Settled: both at reduced salaries | $215,964 | Minimal | $28,427 | $17,183 | $16,521 | $12,280 |

Modeling note (applies to scenarios b, c, d1, d2): maxing out retirement contributions on a single or reduced income is a theoretical case shown for comparability, not a realistic default. A household experiencing an income drop is more likely to fall toward the "minimal" end of the range shown above.

---

## 2. All-In Monthly Housing Cost by Price Point

### Method

- Down payment fixed at $200,000 (actual dollars) across all price points, per `shared/assumptions.md`. Loan amount = price minus $200,000.
- Principal & interest (P&I): standard 30-year fixed amortization formula.
- Mortgage rate, base case: **6.55%**, the Freddie Mac Primary Mortgage Market Survey (PMMS) weekly average for the week ending July 16, 2026 (Freddie Mac PMMS, accessed July 20, 2026). Same-week daily quotes from other trackers ranged 6.49%-6.61%.
- Property tax: **1.00%** effective annual rate applied to purchase price, approximating Multnomah County's 2026 countywide effective average of 0.96% (taxbycounty.com, 2026 county property tax data) for the target neighborhoods (Mt. Tabor, Laurelhurst, Sellwood-Moreland). Actual ZIP-level effective rates in Multnomah County range from 0.78% to 1.81% depending on levy code area.
  - **Oregon-specific caveat:** under Oregon's Measure 50, assessed value (the actual tax base) is capped at 3%/year growth and is **not** reset to the sale price at purchase. This model applies the effective rate to purchase price as a standard planning approximation, consistent with how Portland-area lenders and closing-cost estimators typically quote it; the actual first-year bill depends on the specific property's existing assessed value, which is often below market value in an appreciating neighborhood.
- Homeowners insurance: dwelling (rebuild) coverage assumed at 75% of purchase price, excluding land value, consistent with standard replacement-cost estimation. Base rate uses Oregon dwelling-coverage data points of $1,741/yr at $300K coverage and $2,170/yr at $400K coverage (Insure.com / ValuePenguin-style Oregon homeowners insurance data, 2026), linearly extrapolated, plus a 15% loading for Pacific Northwest wildfire-related reinsurance repricing pressure that is affecting statewide Oregon premiums even outside high-risk zones (OPB, "Oregon homeowners face rising insurance costs as wildfire risk grows," Feb. 2025; Grants Pass Tribune, "Oregon Homeowners Face Compounding Insurance Pressures," 2026). This is a scaled estimate, not a bound quote, and is explicitly not a national-average figure (a generic Portland-wide average of ~$801/yr, reported by Hippo Insurance for 2026, reflects a lower average home value than the $600K-$800K range modeled here and is not used directly).
- Maintenance reserve: standard 1%/year-of-value guideline (widely used real estate/personal finance rule of thumb).
- PMI: applied only if loan-to-value (LTV) exceeds 80%.
- Utilities: reasoned flat estimate of $300/month for a single-family Portland-area home (combined gas, electric, water/sewer, garbage), not itemized further; this is a planning estimate rather than a sourced figure, and will vary with home size and season.

### LTV and PMI Check

| Price | Loan amount | LTV | PMI applicable? |
|---|---|---|---|
| $600,000 | $400,000 | 66.7% | No |
| $650,000 | $450,000 | 69.2% | No |
| $700,000 | $500,000 | 71.4% | No |
| $750,000 | $550,000 | 73.3% | No |
| $800,000 | $600,000 | 75.0% | No |

Because the down payment is a fixed $200,000 rather than a percentage, LTV stays below the 80% PMI threshold at every price point modeled; PMI does not apply in this analysis.

### All-In Monthly Housing Cost (base rate, 6.55%)

| Price | P&I | Property tax | Insurance | Maintenance | PMI | Utilities | **Total monthly** |
|---|---|---|---|---|---|---|---|
| $600,000 | $2,541 | $500 | $229 | $500 | $0 | $300 | **$4,070** |
| $650,000 | $2,859 | $542 | $244 | $542 | $0 | $300 | **$4,486** |
| $700,000 | $3,177 | $583 | $259 | $583 | $0 | $300 | **$4,903** |
| $750,000 | $3,494 | $625 | $275 | $625 | $0 | $300 | **$5,319** |
| $800,000 | $3,812 | $667 | $290 | $667 | $0 | $300 | **$5,736** |

Property tax and maintenance reserve are numerically close to each other in this table because both happen to use a rate near 1% of purchase price; they are computed independently (property tax from the county effective rate, maintenance from the separate 1% rule of thumb) and are not the same line item.

### Closing Costs (Cash Needed at Close, Itemized)

**Method:**

- Origination fee: 1.0% of loan amount (typical Oregon lender origination fee; JVM Lending, 2026).
- Title & closing/settlement company fees (buyer's side): 0.8% of loan amount. Oregon custom has the seller pay the owner's title policy; the buyer's cost here covers the lender's title policy and closing agent fees. (Sammamish Mortgage / JVM Lending Oregon closing cost guides, 2026; owner's title policy alone runs 0.21%-0.45% of price per these sources, for context, though that portion is typically seller-paid.)
- Miscellaneous lender fees: $1,500 flat (appraisal, credit report, recording, flood certification).
- Escrow fee: buyer's half of (purchase price divided by $1,000, plus $1,200), split 50/50 with the seller per Oregon custom (Oregon Real Estate Closing Guide, Quill Title, 2026).
- Prepaid tax/insurance: one full year of homeowners insurance premium paid at closing, plus a 3-month property tax proration (mid-year closing assumption).
- Lender reserves (impound cushion): 2 months of property tax plus 2 months of insurance premium held in the escrow/impound account, standard lender practice.
- This itemization (roughly 2.5%-2.6% of price) sits within, but toward the lower end of, the commonly cited Oregon closing cost range of 2%-4% of purchase price (Sammamish Mortgage, 2026), because prepaid items and lender reserves are shown separately per this analysis's requirements rather than folded into a single "closing cost %" estimate.

| Price | Origination | Title/closing | Misc. fees | Escrow (buyer half) | Prepaid tax/insurance | Lender reserves | **Total cash needed** | % of price |
|---|---|---|---|---|---|---|---|---|
| $600,000 | $4,000 | $3,200 | $1,500 | $900 | $4,242 | $1,457 | **$15,299** | 2.55% |
| $650,000 | $4,500 | $3,600 | $1,500 | $925 | $4,552 | $1,571 | **$16,648** | 2.56% |
| $700,000 | $5,000 | $4,000 | $1,500 | $950 | $4,862 | $1,685 | **$17,998** | 2.57% |
| $750,000 | $5,500 | $4,400 | $1,500 | $975 | $5,172 | $1,800 | **$19,347** | 2.58% |
| $800,000 | $6,000 | $4,800 | $1,500 | $1,000 | $5,482 | $1,914 | **$20,696** | 2.59% |

### Effect on the Emergency Fund If Closing Costs Are Paid From It

The $200,000 down payment pool is fully consumed by the down payment itself, per `shared/assumptions.md`. If closing costs are paid from the $70,000 emergency fund rather than from an outside source, the fund is reduced as follows:

| Price | Closing costs | Emergency fund after closing | % of original $70,000 remaining |
|---|---|---|---|
| $600,000 | $15,299 | $54,701 | 78.1% |
| $650,000 | $16,648 | $53,352 | 76.2% |
| $700,000 | $17,998 | $52,002 | 74.3% |
| $750,000 | $19,347 | $50,653 | 72.4% |
| $800,000 | $20,696 | $49,304 | 70.4% |

The corresponding emergency fund runway in months, and how this reduced balance interacts with income-loss scenarios, is addressed in `06-affordability-assessment/analysis.md` alongside the combined cash flow picture.

---

## 3. Mortgage Rate Sensitivity

### Method

- Base case: 6.55% (Freddie Mac PMMS, week ending July 16, 2026).
- Two stress rates are shown: **+100 basis points (7.55%)** and **+200 basis points (8.55%)**. These increments were chosen because 30-year fixed rates have moved by more than 200 basis points within multi-year windows in the recent past (from roughly 3% in 2021 to nearly 8% at the October 2023 peak, per Freddie Mac/FRED historical series), so a 100-200 bps difference between the rate assumed today and the rate actually available at closing is a plausible planning range, not an extreme tail scenario.
- All other housing cost components (property tax, insurance, maintenance, utilities) are held constant across rate scenarios; only P&I changes. Since PMI does not apply at any price point modeled (Section 2), it stays at $0 across all rate scenarios as well.
- This section shows the effect of rate changes on housing cost alone. It does not net housing cost against income, childcare, or any other cost line; that combined view is built in `06-affordability-assessment/analysis.md`.

### P&I by Price and Rate

| Price | Loan amount | P&I, base (6.55%) | P&I, +100 bps (7.55%) | P&I, +200 bps (8.55%) |
|---|---|---|---|---|
| $600,000 | $400,000 | $2,541 | $2,811 | $3,090 |
| $650,000 | $450,000 | $2,859 | $3,162 | $3,476 |
| $700,000 | $500,000 | $3,177 | $3,513 | $3,862 |
| $750,000 | $550,000 | $3,494 | $3,865 | $4,249 |
| $800,000 | $600,000 | $3,812 | $4,216 | $4,635 |

### Total All-In Monthly Housing Cost by Price and Rate

| Price | Total, base (6.55%) | Total, +100 bps (7.55%) | Total, +200 bps (8.55%) | $ increase, base to +200 bps | % increase, base to +200 bps |
|---|---|---|---|---|---|
| $600,000 | $4,070 | $4,340 | $4,619 | $549 | 13.5% |
| $650,000 | $4,486 | $4,789 | $5,103 | $617 | 13.8% |
| $700,000 | $4,903 | $5,239 | $5,588 | $685 | 14.0% |
| $750,000 | $5,319 | $5,690 | $6,074 | $755 | 14.2% |
| $800,000 | $5,736 | $6,140 | $6,559 | $823 | 14.3% |

A 200 basis point rate increase raises the total all-in monthly housing cost by roughly 13.5%-14.3% across the price points modeled, with the percentage increase rising slightly at higher price points because a larger share of the total monthly cost is P&I (which is rate-sensitive) rather than the roughly rate-independent tax, insurance, maintenance, and utility components.

---

## Sources

- Tax Foundation, "2026 Tax Brackets" (federal MFJ brackets and standard deduction), accessed July 2026: https://taxfoundation.org/data/all/federal/2026-tax-brackets/
- Oregon Department of Revenue, "Oregon Withholding Tax Formulas," Publication 150-206-436, effective January 1, 2026 (Oregon MFJ brackets, standard deduction, federal tax subtraction phase-out schedule): https://www.oregon.gov/dor/forms/FormsPubs/withholding-tax-formulas_206-436_2026.pdf
- Social Security Administration, 2026 contribution and benefit base ($184,500): https://www.ssa.gov/oact/cola/cbb.html
- IRS, Topic No. 751, Social Security and Medicare withholding rates (Additional Medicare Tax threshold): https://www.irs.gov/taxtopics/tc751
- IRS Newsroom, "401(k) limit increases to $24,500 for 2026, IRA limit increases to $7,500": https://www.irs.gov/newsroom/401k-limit-increases-to-24500-for-2026-ira-limit-increases-to-7500
- Freddie Mac, Primary Mortgage Market Survey (PMMS), week ending July 16, 2026 (base mortgage rate): https://www.freddiemac.com/pmms
- FRED (Federal Reserve Bank of St. Louis), 30-Year Fixed Rate Mortgage Average series (historical rate range for stress-test rationale): https://fred.stlouisfed.org/series/MORTGAGE30US
- taxbycounty.com, Multnomah County property tax data, 2026: https://taxbycounty.com/oregon/multnomah-county
- Insure.com / ValuePenguin-style Oregon homeowners insurance dwelling-coverage data, 2026
- OPB, "Oregon homeowners face rising insurance costs as wildfire risk grows," February 2025: https://www.opb.org/article/2025/02/06/oregon-homeowners-face-rising-insurance-costs-wildfire-risk-grows/
- Grants Pass Tribune, "Oregon Homeowners Face Compounding Insurance Pressures as Wildfire Risk and Rising Costs Converge in 2026"
- Hippo Insurance, Portland, Oregon homeowners insurance average premium, 2026 (cited for contrast, not used directly): https://www.hippo.com/homeowners-insurance/oregon/portland
- JVM Lending, "Typical Closing Costs in Oregon for Buyers and Sellers," 2026: https://www.jvmlending.com/blog/typical-closing-costs-in-oregon-for-buyers-and-sellers/
- Sammamish Mortgage, "Average Closing Costs for Home Buyers in Oregon 2026": https://www.sammamishmortgage.com/average-buyer-closing-costs-oregon/
- Quill Title, "Oregon Real Estate Closing Guide" (escrow fee convention): https://www.quilltc.com/blog/oregon-real-estate-closing-guide

## Method Notes Addressed From Known Modeling Issues

This document addresses the subset of issues in `shared/known-modeling-issues.md` relevant to home-purchase cost mechanics; issues specific to childcare, children's health insurance, baseline living expenses, combined cash flow, and emergency fund runway are addressed in `02-future-budget/analysis.md` and `06-affordability-assessment/analysis.md` instead. In particular: Married Filing Jointly brackets are used throughout (issue 3); both spouses' FICA wage bases and the Additional Medicare Tax are applied correctly, including the correction that 401(k) deferrals do not reduce FICA wages (issue 4); closing costs are itemized and shown reducing the emergency fund balance (issue 5); job-loss/reduced-income scenarios use each partner's actual salary or an explicitly labeled hypothetical, never an unstated floor (issues 9, 11); max retirement contributions in reduced-income scenarios are flagged as theoretical (issue 10); homeowners insurance is scaled to the modeled home value with a stated wildfire-pressure loading, not a national average (issue 14); the "both shift to lower-paying jobs" scenario is split into a transition period and a settled state (issue 15); external cost estimates (mortgage rate, property tax, insurance, closing costs) are checked against current, cited sources rather than carried forward as round numbers (issue 19); and the prose throughout states scenario mechanics neutrally, without persuasive or advice-toned framing (issue 20).
