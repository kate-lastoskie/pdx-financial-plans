# 2001 vs. 2026 Home Purchase Comparison: Parents' Ann Arbor Purchase vs. Kate & Lucas's Portland Target

Compares the parents' 2001 home purchase in Ann Arbor, Michigan to Kate & Lucas's 2026 Portland, OR home target across price-to-income, taxes, inflation, childcare, healthcare, and retirement context.

## Inputs used (confirmed facts)

- Parents: 4663 Erin Court, Ann Arbor, Michigan. Purchased 2001 for $540,000. Combined household income at the time: $177,500/yr. State: Michigan (flat-rate income tax).
- Kate & Lucas: targeting a $600,000 to $800,000 Portland, OR home in 2026. Combined gross income: $308,520/yr (Kate $165,000 + Lucas $143,520). Down payment pool: $200,000 actual dollars. Filing status: Married Filing Jointly for both households (assumed for the parents, since MFJ is the applicable status for a two-earner married couple; not separately confirmed but the standard assumption for this analysis).

---

## 1. Price-to-income ratio and mortgage payment as % of gross income

**Method:**
- Price-to-income ratio = home price divided by combined gross annual income.
- Monthly principal and interest (P&I) calculated using the standard fixed-rate amortization formula: P&I = L x r x (1+r)^n / ((1+r)^n - 1), where L = loan amount, r = monthly interest rate, n = number of payments (360 for a 30-year loan).
- 2001 mortgage rate: simple average of the 52 weekly Freddie Mac Primary Mortgage Market Survey (PMMS) 30-year fixed rate readings published during calendar year 2001, retrieved via FRED series MORTGAGE30US (Federal Reserve Bank of St. Louis). Average = 6.97%.
- 2026 mortgage rate: most recent Freddie Mac PMMS 30-year fixed rate as of this analysis, week of July 16, 2026 = 6.55% (Freddie Mac, "Mortgage Rates Average 6.55%," July 16, 2026).
- Down payment for the parents' 2001 purchase is not a confirmed figure. This analysis assumes a standard 20% down payment ($108,000) as a stated, labeled assumption, since no other figure is available.
- Down payment for Kate & Lucas is a confirmed actual dollar figure ($200,000), applied against each price point in the target range, per shared/assumptions.md.

**Table:**

| Metric | Parents (2001) | Kate & Lucas (2026), $600K | Kate & Lucas (2026), $700K (midpoint) | Kate & Lucas (2026), $800K |
|---|---|---|---|---|
| Home price | $540,000 | $600,000 | $700,000 | $800,000 |
| Combined gross income | $177,500 | $308,520 | $308,520 | $308,520 |
| Down payment | $108,000 (20%, assumed) | $200,000 (actual) | $200,000 (actual) | $200,000 (actual) |
| Loan amount | $432,000 | $400,000 | $500,000 | $600,000 |
| Loan-to-value | 80.0% | 66.7% | 71.4% | 75.0% |
| Mortgage rate | 6.97% (2001 annual avg., Freddie Mac PMMS) | 6.55% (Freddie Mac PMMS, week of 7/16/2026) | 6.55% | 6.55% |
| Monthly P&I | $2,865 | $2,541 | $3,177 | $3,812 |
| Annual P&I | $34,378 | $30,497 | $38,122 | $45,746 |
| P&I as % of gross income | 19.4% | 9.9% | 12.4% | 14.8% |
| Price-to-income ratio | 3.04x | 1.94x | 2.27x | 2.59x |

At every price point in the target range, the price-to-income ratio and the P&I-to-income ratio are lower for Kate & Lucas than they were for the parents in 2001, on a pre-tax, mortgage-only basis. This does not include property tax, insurance, HOA, maintenance, PMI, or other carrying costs, which are addressed in the home affordability analysis (03-home-affordability/).

---

## 2. Income tax comparison

**Method, federal:**
- 2001: the Economic Growth and Tax Relief Reconciliation Act of 2001 (EGTRRA) was signed into law on June 7, 2001, but its rate changes were made retroactive to January 1, 2001. The rate schedule actually used to compute 2001 tax liability (filed in spring 2002) reflects EGTRRA's rates, not the pre-EGTRRA 2000 rates. This analysis uses the actual 2001 Married Filing Jointly schedule: 15% / 27.5% / 30.5% / 35.5% / 39.1% (Tax Foundation, "Federal Individual Income Tax Rates History, Nominal Dollars, Income Years 1913-2013"). 2001 standard deduction for a married couple: $7,600 (Tax Policy Center, "Standard Deduction Amount, Tax Years 1970-2024," sourced to IRS Revenue Procedures). 2001 personal exemption: $2,900 per person (IRS Rev. Proc. 2001-13). This analysis assumes 2 personal exemptions (self + spouse); the number of dependents the parents claimed in 2001 is not confirmed, so no dependent exemptions are added. This is a stated simplification, not a confirmed fact.
- 2026: current federal Married Filing Jointly brackets under the permanent Tax Cuts and Jobs Act rate structure (made permanent by the One Big Beautiful Bill Act), with the routine 2026 inflation adjustment per IRS Revenue Procedure 2025-32: 10% / 12% / 22% / 24% / 32% / 35% / 37%, standard deduction $32,200 (compiled by PennyCalc.com against IRS Rev. Proc. 2025-32, last verified May 9, 2026).

**Method, state:**
- 2001 Michigan: flat individual income tax rate of 4.2%, which applied for tax years 2000 and 2001 (Michigan Senate Fiscal Agency, "State Notes: History of the Michigan Individual Income Tax Rate," 2015). This is lower than Michigan's current flat rate of 4.25% (in effect since 2024, after a one-year reduction to 4.05% for 2023 only). This analysis applies Michigan's 2001 rate to gross income less an estimated $5,800 in personal exemptions (2 x $2,900, used as an approximation for Michigan's own exemption amount, which was not separately confirmed; the dollar effect of this simplification is minor, on the order of $240 in tax).
- 2026 Oregon: Married Filing Jointly brackets: 4.75% up to $8,600, 6.75% up to $21,500, 8.75% up to $250,000, 9.9% above $250,000; standard deduction $5,670 (Oregon Department of Revenue 2026 tables, compiled by TaxFormCalculator.com). Oregon's federal-tax subtraction (a deduction for federal taxes paid) phases out completely at higher incomes and is assumed to be $0 at this household's income level.

**Method, FICA:**
- 2001: Social Security (OASDI) wage base $80,400 per earner (SSA, "2001 Social Security/SSI/Medicare Information" fact sheet), 6.2% each side. Medicare 1.45%, uncapped. No Additional Medicare Tax existed in 2001 (it was introduced by the ACA effective 2013). Because the parents' individual (per-earner) incomes are not confirmed, this analysis assumes the $177,500 was split evenly between two earners for SS wage-base purposes; this is a stated assumption.
- 2026: Social Security wage base $184,500 per earner (SSA Contribution and Benefit Base, 2026), applied separately to Kate's $165,000 and Lucas's $143,520. Medicare 1.45% uncapped, plus the Additional Medicare Tax of 0.9% on combined wages above the $250,000 MFJ threshold (unindexed for inflation since 2013).

**Table:**

| Item | Parents (2001) | Kate & Lucas (2026) |
|---|---|---|
| Combined gross income | $177,500 | $308,520 |
| Federal taxable income | $164,100 | $276,320 |
| Federal income tax | $41,123 | $51,513 |
| State taxable income | $165,900 (approx., after est. exemptions) | $302,850 |
| State income tax | $7,211 (Michigan, 4.2% flat) | $26,505 (Oregon, bracketed) |
| FICA (Social Security + Medicare) | $12,543 | $24,128 |
| Total tax | $60,878 | $102,146 |
| Effective combined tax rate (on gross income) | 34.3% | 33.1% |
| Net (after-tax) income, annual | $116,622 | $206,374 |
| Net (after-tax) income, monthly | $9,719 | $17,198 |

On a nominal, gross-income basis, the combined effective tax burden (federal + state + FICA) is very similar between the two households: 34.3% for the parents in 2001 versus 33.1% for Kate & Lucas in 2026, a difference of about 1.2 percentage points, with the parents' rate higher. This is a materially different picture from a comparison that assumes zero state income tax for the parents (as the prior, incorrect draft did). Michigan's 4.2% flat rate and Oregon's bracketed rate (which produces an effective state rate on this specific income level of roughly 8.6%, well below Oregon's 9.9% top marginal rate) both factor into the totals above.

---

## 3. Inflation adjustment (CPI)

**Method:**
- Index used: CPI-U (Consumer Price Index for All Urban Consumers), U.S. city average, all items, 1982-84=100 (U.S. Bureau of Labor Statistics).
- 2001 value: annual average of 177.1 (BLS historical CPI-U table).
- 2026 value: the most recent available reading at the time of this analysis is the April 2026 index of 333.020 (not seasonally adjusted), from BLS CPI news release Table 1, published May 12, 2026. A full-year 2026 annual average is not yet available, so the latest published month is used per the task's stated fallback methodology.
- Multiplier = 333.020 / 177.1 = 1.8804. In other words, $1.00 in 2001 had the same purchasing power as approximately $1.88 in April 2026 dollars.

**Table:**

| 2001 figure | Nominal (2001 $) | 2026-equivalent ($, using 1.8804 multiplier) |
|---|---|---|
| Home price | $540,000 | $1,015,420 |
| Combined gross income | $177,500 | $333,772 |
| Monthly net (after-tax) take-home | $9,719 | $18,275 |

The parents' $540,000 2001 home price is equivalent to roughly $1.02 million in April 2026 dollars, which is above the entire $600,000 to $800,000 range Kate & Lucas are considering. On a real (inflation-adjusted) basis, the Portland target home is cheaper than the parents' home was, at every price point in the range.

The parents' nominal monthly net take-home of $9,719 converts to about $18,275 in 2026 dollars, compared to Kate & Lucas's nominal monthly net take-home of $17,198. In real terms, the parents' after-tax monthly income was about $1,077 higher than Kate & Lucas's projected after-tax monthly income, a gap of roughly $12,924/year. This gap reflects the combined effect of the tax burden difference calculated in Section 2, FICA base differences, and the fact that gross income did not grow by the full CPI multiplier (a multiplier of 1.8804 applied to $177,500 would imply $333,772 to keep pace with inflation alone; actual combined income is $308,520, about 7.6% below that inflation-adjusted benchmark).

---

## 4. Childcare cost comparison

**Method:**
- 2026 Portland figures are sourced from current childcare cost aggregator data for the Portland, OR metro area (center-based care): infant care approximately $1,560/month (daycarecalc.com, 2026 Portland city data), preschool-age care approximately $1,200/month (midpoint of a $1,128 to $1,477/month range reported across multiple 2026 Portland childcare cost sources).
- 2001 figures could not be found as precise, citable, Ann Arbor-specific numbers. This analysis uses labeled estimates of $550/month for infant center-based care and $450/month for preschool center-based care in 2001, based on general knowledge of national childcare cost levels in the early 2000s (a period when full-time center-based infant care commonly ran in the $400 to $700/month range nationally, with the Midwest typically at or below the national average). These are estimates, not sourced figures, and are flagged as such.
- Real (inflation-adjusted) comparison uses the CPI multiplier of 1.8804 from Section 3.
- Per known-modeling-issues.md, a 2-year age gap between two children means the two are never both in infant care simultaneously; the relevant comparison is one infant plus one preschooler ("infant + preschool overlap"), not "infant care x2."

**Table:**

| | 2001 estimate (nominal) | 2001 estimate in 2026 dollars | 2026 (sourced) | Real (inflation-adjusted) change |
|---|---|---|---|---|
| Infant center care, per month | $550 | $1,034 | $1,560 | +50.8% above inflation |
| Preschool center care, per month | $450 | $846 | $1,200 | +41.8% above inflation |
| Combined (1 infant + 1 preschooler), per month | $1,000 | $1,880 | $2,760 | +46.8% above inflation |

Childcare costs for a comparable arrangement (center-based, one infant and one preschooler) appear to have grown by roughly 47% more than general inflation between 2001 and 2026, based on the estimates above. This figure should be treated as directional rather than precise, given the absence of a confirmed 2001 baseline specific to Ann Arbor. Portland's Multnomah County "Preschool for All" program, which offers free preschool for eligible 3- and 4-year-olds, could reduce the 2026 preschool figure substantially for a qualifying family; this was not built into the $1,200/month figure above, which reflects private-pay center care.

---

## 5. Healthcare premium comparison

**Method:**
- 2026 figure: KFF (Kaiser Family Foundation) 2025 Employer Health Benefits Survey (the most recent published survey as of this analysis), which reported an average worker contribution toward family coverage of approximately $6,850/year (KFF, "Annual Family Premiums for Employer Coverage Rise 6% in 2025, Nearing $27,000, with Workers Paying $6,850 Toward Premiums Out of Their Paychecks," 2025).
- 2001 figure: a precise 2001 dollar figure from the original KFF/HRET survey report was not directly retrievable in this research pass. A defensible estimate is derived from a documented KFF data point stating that the 2010 average worker contribution to family coverage (~$3,997/year) was roughly double the 2001 amount, implying a 2001 figure of approximately $1,787 to $2,000/year. This analysis uses $1,787/year as a labeled estimate.
- Real (inflation-adjusted) comparison uses the CPI multiplier of 1.8804 from Section 3.

**Table:**

| | 2001 estimate (nominal, annual) | 2001 estimate in 2026 dollars | 2026 (sourced, annual) | Real (inflation-adjusted) change |
|---|---|---|---|---|
| Employee contribution, family coverage | ~$1,787 | ~$3,360 | ~$6,850 | +103.9% above inflation |
| Employee contribution, family coverage (monthly) | ~$149 | ~$280 | ~$571 | +103.9% above inflation |

The employee-paid share of family health coverage appears to have roughly doubled in real (inflation-adjusted) terms between 2001 and 2025/2026, based on KFF survey data. The 2001 figure here is an estimate derived from a secondary KFF data comparison rather than a direct citation of the original 2001 survey report, and should be treated accordingly.

---

## 6. Retirement savings context

Defined-benefit (pension) plans were more prevalent among private-sector workers in 2001 than they are in 2026; the shift toward defined-contribution plans (401(k) and similar) as the primary employer-sponsored retirement vehicle has been well documented by the Bureau of Labor Statistics and the Employee Benefit Research Institute over this period. This shift generally means a smaller share of retirement funding responsibility fell on individual savings and investment decisions in 2001 than it does now, all else equal.

This analysis does not have confirmed data on whether the parents specifically had access to a defined-benefit pension in 2001, or what portion of the parents' income (if any) went to retirement savings at the time of the 2001 purchase. This section is included as documented historical and structural context per the task requirements, not as a quantified line item in the income/expense comparison, and should not be read as a claim about the parents' specific retirement arrangement.

---

## 7. Summary comparison table

| Metric | Parents (2001) | Kate & Lucas (2026, $700K midpoint) |
|---|---|---|
| Home price | $540,000 | $700,000 |
| Home price, 2026-equivalent dollars (CPI 1.8804x) | $1,015,420 | $700,000 (already in 2026 dollars) |
| Combined gross income | $177,500 | $308,520 |
| Combined gross income, 2026-equivalent dollars | $333,772 | $308,520 |
| Price-to-income ratio | 3.04x | 2.27x |
| Mortgage rate (30-yr fixed) | 6.97% (2001 annual avg.) | 6.55% (July 2026) |
| Monthly P&I | $2,865 | $3,177 |
| P&I as % of gross income | 19.4% | 12.4% |
| Combined effective tax rate (federal + state + FICA) | 34.3% | 33.1% |
| Net monthly take-home (nominal) | $9,719 | $17,198 |
| Net monthly take-home, 2026-equivalent dollars | $18,275 | $17,198 |

On the metrics available for direct comparison: the home price-to-income ratio and mortgage-payment-to-income ratio were both higher for the parents in 2001 than the corresponding figures for Kate & Lucas's $700,000 Portland scenario in 2026. The combined effective tax rate was slightly higher for the parents (34.3%) than for Kate & Lucas (33.1%), a modest difference once Michigan's actual 2001 state income tax is included, in contrast to a comparison that incorrectly assumed no state income tax for the parents. In real (inflation-adjusted) terms, the parents' monthly net take-home income was higher than Kate & Lucas's projected monthly net take-home, a gap driven primarily by combined gross income not keeping pace with the CPI-measured inflation multiplier over this 25-year period, rather than by a state income tax differential. Childcare and the employee share of health insurance premiums both appear to have grown faster than general inflation over the same period, based on the sourced and estimated figures in Sections 4 and 5.

---

## Sources cited

- Freddie Mac Primary Mortgage Market Survey (PMMS), weekly 30-year fixed mortgage rate data, retrieved via FRED series MORTGAGE30US, Federal Reserve Bank of St. Louis (accessed July 2026); Freddie Mac, "Mortgage Rates Average 6.55%," news release, July 16, 2026.
- Tax Foundation, "Federal Individual Income Tax Rates History, Nominal Dollars, Income Years 1913-2013."
- Tax Policy Center, "Standard Deduction Amount, Tax Years 1970-2024" (sourced to IRS Revenue Procedures).
- IRS Revenue Procedure 2001-13 (2001 personal exemption amount, $2,900).
- Economic Growth and Tax Relief Reconciliation Act of 2001 (EGTRRA), enacted June 7, 2001, retroactive to January 1, 2001.
- PennyCalc.com, "2026 Federal Tax Brackets and Standard Deduction," verified against IRS Revenue Procedure 2025-32, last updated May 9, 2026.
- Michigan Senate Fiscal Agency, "State Notes: History of the Michigan Individual Income Tax Rate," 2015.
- Oregon Department of Revenue 2026 personal income tax brackets, compiled via TaxFormCalculator.com, "Oregon Tax Tables 2026."
- Social Security Administration, "2001 Social Security/SSI/Medicare Information" fact sheet (2001 OASDI wage base, $80,400).
- Social Security Administration, "Contribution and Benefit Base" (2026 OASDI wage base, $184,500).
- U.S. Bureau of Labor Statistics, CPI-U historical annual average table (2001 value, 177.1) and CPI news release Table 1 (April 2026 value, 333.020), published May 12, 2026.
- KFF (Kaiser Family Foundation), "Annual Family Premiums for Employer Coverage Rise 6% in 2025, Nearing $27,000, with Workers Paying $6,850 Toward Premiums Out of Their Paychecks," 2025 Employer Health Benefits Survey.
- KFF, "Average Annual Worker and Employer Contributions to Premiums and Total Premiums for Family Coverage, 1999-2012" (used to derive the 2001 healthcare estimate).
- Portland, OR childcare cost data (2026): daycarecalc.com and multiple aggregator sources for Portland-area infant and preschool center-based care rates.
- 2001 childcare cost figures: labeled estimates, not directly sourced (see Section 4).
- Bureau of Labor Statistics / Employee Benefit Research Institute: general trend data on defined-benefit vs. defined-contribution retirement plan prevalence (see Section 6; not independently re-verified for exact figures in this pass).
