# Seattle Condo: Keep or Sell

Property: 1740 NE 86th St #319, Maple Leaf, Seattle, WA 98115 ("Lakeside North" building). 641 sq ft, 1BR/1BA, elevator building, in-unit washer/dryer, covered parking, built 1982. Purchased August 2022 for $339,000. Remaining loan balance $305,000.

This document covers carrying costs, rental economics, tax mechanics, sale economics, a 5-year hold-vs-sell comparison, and how the decision interacts with the Portland home purchase.

---

## 1. Current Carrying Cost

**Method:**
- The baseline monthly carrying cost was supplied as a given input (`shared/assumptions.md`): PITI $2,017, HOA $435, maintenance reserve ~$283/month.
- A live listing for the unit itself, current mortgage-rate data, or the original loan documents were not available to this analysis, so the PITI figure is used as given rather than independently re-derived from the original note.
- As a plausibility check only (not a substitute for the given figure), the components were estimated separately: principal & interest on a $305,000 balance assuming a 5.4% rate (the Freddie Mac 30-year fixed average for August 2022 was 5.22% on Aug 11 and 5.55% on Aug 25, so 5.4% is a reasonable midpoint; source: Freddie Mac Primary Mortgage Market Survey archive, accessed July 2026) and roughly 26 years remaining amortization, plus an estimated King County property tax of about 0.92% of the $339,000 purchase value, plus an estimated $45/month condo (HO-6) insurance premium.
- This plausibility check produces an estimated PITI of about $2,126/month, close to but not identical to the given $2,017/month baseline. The gap is expected: the actual loan's rate, term, and escrow amounts are not known precisely, and property tax/insurance estimates are approximations. The analysis below uses the given $2,017 baseline, not the plausibility-check estimate.

**Carrying cost breakdown:**

| Item | Monthly | Annual |
|---|---|---|
| PITI (principal, interest, taxes, insurance) | $2,017 | $24,204 |
| HOA dues | $435 | $5,220 |
| Maintenance reserve (~1.5%/yr of value, estimated) | $283 | $3,396 |
| **Total carrying cost** | **$2,735** | **$32,820** |

| Plausibility check (estimate only, not used downstream) | Monthly |
|---|---|
| Estimated P&I ($305,000 balance, 5.4% assumed rate, ~26 yrs remaining) | $1,821 |
| Estimated property tax (0.92% of $339,000 est.) | $260 |
| Estimated insurance (HO-6, estimate) | $45 |
| Estimated PITI total | $2,126 |
| Given baseline PITI (used in this analysis) | $2,017 |

---

## 2. Rental Scenarios

**Method for establishing a rent range:**
- Same-building listings were pulled directly (Apartments.com, accessed July 2026) since they are the most directly comparable data available for this specific unit.
- Redfin's automated rent estimate for the subject unit itself was also pulled (Redfin, accessed July 2026).
- Broader neighborhood and zip-code rent data were pulled as secondary context, since they include unit types and buildings that are not directly comparable (different vintage, size, amenities).

**Rent comps found:**

| Unit / Source | Size | Features | Asking Rent | Source, Date |
|---|---|---|---|---|
| #106 (same building) | 643 sq ft, 1BR/1BA | Ground floor, elevator building, gated, no covered parking mentioned | $1,490/mo | Apartments.com, listing updated Jul 20, 2026 |
| #102 (same building) | 650 sq ft, 1BR/1BA | Ground floor, in-unit W/D, covered parking, water/sewer included | $1,595/mo | Apartments.com, listing updated Jul 20, 2026 |
| #310 (same building, closest match to #319) | 641 sq ft, 1BR/1BA | Top floor, elevator, in-unit W/D, covered parking (matches #319's size and features most closely) | $2,160/mo | Apartments.com, listing updated Jun 16, 2026 |
| #319 (subject unit) | 641 sq ft | Automated rent estimate | $1,893 to $2,373/mo | Redfin, accessed Jul 2026 |
| Zip 98115, 1BR (all buildings) | - | - | avg $2,092 / median $2,103/mo | RentCafe, accessed Jul 2026 |
| Maple Leaf neighborhood, 1BR (all buildings) | - | - | avg $1,991/mo (range $1,400 to $2,855) | Apartments.com neighborhood data, accessed Jul 2026 |

Note: Redfin's automated valuation tools (including rent estimates) carry a stated error margin of roughly 7% on value estimates for off-market properties (Redfin, accessed Jul 2026); the estimate range above should be read with that in mind.

**Rent scenario definitions used below:** Pessimistic $1,700/mo (below all comps except the two lowest, ground-floor units), Base $2,000/mo (within the Redfin estimate range and below the closest same-unit-type comp), Optimistic $2,200/mo (near the #310 comp and the zip-code median).

**Method for net cash flow:**
- Raw net = monthly rent minus the $2,735 carrying cost.
- Vacancy loss = rent x 7.3%, the U.S. Census Bureau's national rental vacancy rate for Q1 2026 (Census Bureau, Housing Vacancies and Homeownership report, released 2026). This is a national figure, not Seattle-specific; a Seattle-specific vacancy rate was not readily available, so this is a labeled estimate.
- Property management fee = 10% of effective (post-vacancy) rent, the midpoint of the commonly cited 8-12% range for residential property managers (ClearLead Digital and AllPropertyManagement.com 2026 fee surveys, accessed Jul 2026). This fee is optional and applies only if the couple hires a property manager rather than self-managing; both cases are shown below.

**Net monthly cash flow by scenario:**

| Scenario | Rent | Raw Net (rent - carry) | Vacancy Loss (7.3%) | Effective Rent (after vacancy) | Net After Vacancy (self-managed) | PM Fee (10% of effective rent, if hired) | Net After Vacancy + PM (professionally managed) |
|---|---|---|---|---|---|---|---|
| Pessimistic | $1,700 | -$1,035 | $124 | $1,576 | -$1,159 | $158 | -$1,317 |
| Base | $2,000 | -$735 | $146 | $1,854 | -$881 | $185 | -$1,066 |
| Optimistic | $2,200 | -$535 | $161 | $2,039 | -$696 | $204 | -$900 |

In every scenario researched, monthly rent (even before vacancy or management fees) is below the $2,735 carrying cost. Adding vacancy loss and, if applicable, a property manager's fee widens the monthly shortfall further.

---

## 3. Rental Income Taxability

**Federal tax mechanics:**
- Rental income is reported on Schedule E and is taxable at the federal level regardless of state.
- Deductible items that reduce taxable rental income include mortgage interest, property tax, insurance, HOA dues, maintenance/repairs, property management fees, and depreciation.
- Depreciation: residential rental property is depreciated straight-line over 27.5 years (IRS Publication 527, 2025 edition, accessed Jul 2026), applied only to the building value, not land.
  - Using an estimated 85% building / 15% land allocation (a typical range for a condo unit, where land is a small shared allocation; the exact split would come from the King County assessor's valuation breakdown, which was not available to this analysis), the depreciable basis is about $288,150 (85% of the $339,000 purchase price).
  - Annual straight-line depreciation: about $10,478/year ($288,150 / 27.5).

| Depreciation estimate | Amount |
|---|---|
| Purchase price | $339,000 |
| Estimated depreciable basis (85% building) | $288,150 |
| Annual depreciation (27.5-yr straight-line) | $10,478 |

**Passive activity loss limitation:**
- Rental real estate losses are classified as passive losses under IRC Section 469. There is a special allowance of up to $25,000/year for actively-participating owners, but it phases out as modified adjusted gross income (MAGI) rises from $100,000 to $150,000, and is fully eliminated at MAGI of $150,000 or more (IRS Publication 925, 2025 edition, accessed Jul 2026).
- The household's combined gross income is $308,520/year (per `shared/assumptions.md`), well above the $150,000 phase-out ceiling.
- Practical effect: because depreciation (~$10,478/year) is large relative to the near-breakeven-to-negative cash flow shown in Section 2, the rental is likely to show a tax loss on paper in most of the scenarios modeled. At this household's income level, that loss is not currently deductible against W-2 wages. It becomes a suspended passive loss that carries forward and can only offset passive income in future years or be released against gain when the property is eventually sold.
- Net effect on current-year taxes: because the loss is suspended rather than usable, the realistic near-term effect on the couple's federal tax bill from operating the rental is close to $0 in most years modeled: no additional tax is owed (there is no positive taxable income to tax), but there is also no current-year tax benefit from the paper loss.

**Depreciation recapture on eventual sale:**
- Depreciation taken over the holding period reduces the property's adjusted basis (adjusted basis = purchase price minus accumulated depreciation). If the property is sold for more than the adjusted basis, even if the sale price is below the original $339,000 purchase price, that portion of the difference can be a taxable gain, taxed under unrecaptured Section 1250 gain rules at up to 25% federally (IRS Publication 527, accessed Jul 2026). This is addressed quantitatively in Section 5.

**Washington-specific considerations:**
- Washington has no state income tax, so rental profit (if any) is not taxed at the state income level.
- Washington's capital gains excise tax (7% above an indexed threshold, $278,000 for 2025) explicitly exempts all real estate transactions, including rental property (Washington Department of Revenue, "Capital gains tax," accessed Jul 2026). Real Estate Excise Tax (REET), covered in Section 4, is a separate tax that applies regardless of gain or loss.
- Business & Occupation (B&O) tax: Washington DOR's standing guidance states that leases or rentals of real estate (30-day-or-longer tenancies with exclusive possession) are not subject to B&O tax or retail sales tax; this exemption is broad and not scaled to a minimum size (Washington DOR, "Rental vs. license to use real estate," accessed Jul 2026).
- A newer, separate law (SB 6136, effective January 1, 2025) created a specific B&O tax on residential and commercial rental income, at a rate of 1.5% to 1.75% of gross rental proceeds, but only for landlords with $1,000,000 or more in taxable rental activity in the prior year (wa-law.org bill summary, accessed Jul 2026). A single condo grossing roughly $20,000 to $26,000/year in rent (per Section 2) is far below this $1,000,000 threshold. Based on this, the new landlord B&O tax does not apply at this scale.

**Realistic range of effective additional tax cost:**
- Federal: likely close to $0/year in most scenarios modeled, because the paper loss from depreciation is suspended rather than currently usable (see passive activity loss discussion above), and because there is no current-year taxable rental profit to tax.
- Washington: $0 (no state income tax; B&O tax does not apply at this rental volume based on the $1,000,000 threshold).
- This could change if: rent rises enough to produce positive taxable income after depreciation and expenses (unlikely at the rent levels modeled here), or if the property is sold (see depreciation recapture, addressed in Section 5).

---

## 4. Sale Economics

**Current Seattle-area market conditions:**

| Indicator | Reading | Source, Date |
|---|---|---|
| Seattle condo median sales price (citywide, "traditional" condo segment) | $469,950 | Seattle housing market report (April 2026 data), accessed Jul 2026 |
| Seattle condo days on market | ~40 days average | Seattle housing market report (June 2026 data), accessed Jul 2026 |
| Seattle condo months of supply | 6.2 months (residential homes are at 3.2 months by comparison) | Seattle housing market report (June 2026 data), accessed Jul 2026 |
| Year-over-year condo price trend (citywide) | Roughly -4% year over year (April 2026) | Seattle housing market report, accessed Jul 2026 |

A citywide condo median of $469,950 is not representative of a 641 sq ft, 1982-vintage unit in this specific building; it reflects the broader condo mix including larger, newer, downtown high-rise units. Building-specific comps below are a closer proxy for this unit.

**Same-building sale comps:**

| Unit | Size | Asking Price | Implied $/sq ft | Source, Date |
|---|---|---|---|---|
| #308 | Comparable 1BR unit in same building | $295,000 | Not confirmed (sq ft not verified) | John L Scott Ballard listing, accessed Jul 2026 |
| #301 | 863 sq ft, 2BR/1BA | $364,999 | ~$423/sq ft | Zillow listing, accessed Jul 2026 |

Applying the #301 unit's $423/sq ft to #319's 641 sq ft gives an extrapolated value of roughly $271,000; the #308 listing at $295,000 is a more direct (though unverified for exact square footage) same-building 1BR data point. Both suggest a current value meaningfully below the $339,000 2022 purchase price, consistent with the citywide condo market softening noted above. No single data point here is precise; the three price scenarios below span this uncertainty.

**Method for net proceeds:**
- REET (Real Estate Excise Tax): Washington's state REET is graduated, but all sale scenarios modeled here fall under the $525,000 first bracket, so a flat 1.10% state rate applies (Washington DOR REET rate schedule effective Jan 1, 2026, accessed Jul 2026). King County's local REET add-on is 0.50% (King County / MRSC, accessed Jul 2026). Combined rate used: 1.60%.
- Agent commission: the 2026 national average total commission is about 5.7% (roughly 2.9% listing agent + 2.8% buyer's agent), per a 2026 commission survey (Clever Real Estate / HomeLight data, accessed Jul 2026). Commission rates are negotiable and not fixed by law; 5.7% is used here as a representative current figure, not a guarantee.
- Closing costs and misc (title, escrow, recording): estimated at a flat $2,000, a round-number estimate; actual costs vary by title company and are not separately itemized here.
- Loan payoff: $305,000 (given).

**Net proceeds and cash to/from seller at three price scenarios:**

| | Pessimistic | Base | Optimistic |
|---|---|---|---|
| Sale price | $280,000 | $300,000 | $325,000 |
| REET (1.60% combined) | -$4,480 | -$4,800 | -$5,200 |
| Agent commission (5.7%) | -$15,960 | -$17,100 | -$18,525 |
| Closing costs & misc (estimate) | -$2,000 | -$2,000 | -$2,000 |
| Net proceeds before loan payoff | $257,560 | $276,100 | $299,275 |
| Less: loan payoff | -$305,000 | -$305,000 | -$305,000 |
| **Cash to (+) / needed from (-) seller at closing** | **-$47,440** | **-$28,900** | **-$5,725** |

In all three price scenarios modeled, a sale today would require bringing cash to closing rather than receiving proceeds, because the loan payoff plus transaction costs exceed the estimated sale price in each case.

**Capital gains at these price points:** all three sale prices are below the $339,000 original purchase price, and (assuming the sale happens soon, before much depreciation accumulates) below or near the current basis, so little to no federal capital gains tax would apply on a near-term sale under these scenarios. Washington has no capital gains tax on real estate regardless. This changes if the property is held and depreciated for several years first; see Section 5.

---

## 5. Multi-Year Hold-vs-Sell Comparison (5 Years)

**Method for cumulative cash drain:**
- Uses the monthly net cash flow figures from Section 2, multiplied by 60 months, shown both self-managed and professionally managed.

| Scenario | Monthly Net (self-managed, after vacancy) | 5-Yr Cumulative (self-managed) | Monthly Net (managed, after vacancy + PM fee) | 5-Yr Cumulative (managed) |
|---|---|---|---|---|
| Pessimistic | -$1,159 | -$69,546 | -$1,317 | -$79,001 |
| Base | -$881 | -$52,860 | -$1,066 | -$63,984 |
| Optimistic | -$696 | -$41,736 | -$900 | -$53,972 |

**Method for principal paydown:**
- Using the same 5.4% rate assumption from Section 1 (Freddie Mac, Aug 2022 average) and amortizing the $305,000 balance forward 60 months.

| | 5-Year Estimate |
|---|---|
| Principal paid down (60 months) | $30,830 |
| Estimated loan balance after 5 years | $274,170 |

**Depreciation and adjusted basis over 5 years:**
- Continuing the $10,478/year depreciation estimate from Section 3 across 5 years reduces the adjusted basis, which affects the taxable gain/loss calculation at a future sale even if the sale price stays below the original $339,000 purchase price.

| | Amount |
|---|---|
| Accumulated depreciation (5 years) | $52,391 |
| Adjusted basis after 5 years ($339,000 - $52,391) | $286,609 |

| If sold after 5 years at: | Sale Price | Adjusted-Basis Gain/(Loss) |
|---|---|---|
| Pessimistic | $280,000 | -$6,609 (loss) |
| Base | $300,000 | +$13,391 (taxable gain) |
| Optimistic | $325,000 | +$38,391 (taxable gain) |

Note: at the base and optimistic 5-year sale prices, a taxable gain exists under the adjusted-basis calculation even though the sale price is below the original $339,000 purchase price, because 5 years of depreciation lowered the basis. This gain would be subject to unrecaptured Section 1250 treatment (up to 25% federal) to the extent of accumulated depreciation.

**Price recovery assumption (explicitly an assumption, not a projection):**
- No source in this analysis predicts future Seattle condo prices with confidence. The three appreciation scenarios below are illustrative brackets only, applied to an assumed current value of $300,000 (the "Base" sale-price scenario from Section 4).

| Scenario | Cumulative Change | Assumed Future Value (5 yrs) | Nominal $ Change |
|---|---|---|---|
| Flat | 0% | $300,000 | $0 |
| Modest recovery | +10% | $330,000 | +$30,000 |
| Stronger recovery | +20% | $360,000 | +$60,000 |

**Net 5-year position (cumulative cash drain + principal paydown + assumed value change), professionally managed:**

| Rental Scenario | Appreciation Scenario | 5-Yr Cash Drain | Principal Paydown | Value Change | Net 5-Yr Position |
|---|---|---|---|---|---|
| Pessimistic | Flat | -$79,001 | +$30,830 | $0 | -$48,172 |
| Pessimistic | Modest recovery | -$79,001 | +$30,830 | +$30,000 | -$18,172 |
| Pessimistic | Stronger recovery | -$79,001 | +$30,830 | +$60,000 | +$11,828 |
| Base | Flat | -$63,984 | +$30,830 | $0 | -$33,154 |
| Base | Modest recovery | -$63,984 | +$30,830 | +$30,000 | -$3,154 |
| Base | Stronger recovery | -$63,984 | +$30,830 | +$60,000 | +$26,846 |
| Optimistic | Flat | -$53,972 | +$30,830 | $0 | -$23,143 |
| Optimistic | Modest recovery | -$53,972 | +$30,830 | +$30,000 | +$6,857 |
| Optimistic | Stronger recovery | -$53,972 | +$30,830 | +$60,000 | +$36,857 |

This matrix does not include the depreciation-recapture tax effect on the value-change component (the adjusted-basis table above shows that effect separately, since it depends on the eventual sale price, not the appreciation assumption alone). Net 5-year position ranges from roughly -$48,000 to +$37,000 across the combinations modeled, depending on which rental and appreciation assumptions are used.

---

## 6. Interaction With the Portland Purchase

**Mechanics if sold:**
- The down payment pool for the Portland purchase is $200,000 (per `shared/assumptions.md`).
- If a sale produces a shortfall (cash needed at closing, per Section 4's negative figures) and that shortfall is paid from the down payment pool, the pool is reduced by that amount before the Portland purchase.
- If a sale produces a surplus (positive cash to seller), that amount adds to the pool.

| Sale Scenario | Cash To (+) / Needed From (-) Seller at Closing | Down Payment Pool After (if this comes from/adds to the $200,000 pool) |
|---|---|---|
| Pessimistic ($280,000 sale) | -$47,440 | $152,560 |
| Base ($300,000 sale) | -$28,900 | $171,100 |
| Optimistic ($325,000 sale) | -$5,725 | $194,275 |

A reduced down payment pool means a larger mortgage loan amount on the Portland purchase (at whatever price point is chosen in that range), which increases the Portland monthly mortgage payment. The resulting Portland mortgage payment is calculated in the home-affordability analysis (`03-home-affordability/`), which should treat the down payment pool as a variable input rather than a fixed $200,000 if the condo is sold at a shortfall.

**Mechanics if kept as a rental:**
- The condo's carrying cost continues regardless of whether it is rented (Section 1: $2,735/month).
- If rented, ongoing monthly cash flow is negative in every scenario modeled (Section 2), meaning the condo adds a recurring monthly cash outflow on top of whatever the Portland mortgage and living expenses require.

| Rental Scenario | Ongoing Monthly Net Cash Flow (professionally managed, after vacancy + PM fee) |
|---|---|
| Pessimistic | -$1,317 |
| Base | -$1,066 |
| Optimistic | -$900 |

- This monthly figure would need to be added as a fixed line item to any household cash-flow model that includes both the Portland mortgage and the Seattle condo, alongside the couple's other planned expenses (see `01-current-budget/` and `02-future-budget/` for the household cash-flow context this fits into).
- Keeping the condo also preserves the $200,000 pool intact for the Portland purchase (no shortfall to cover), and preserves the possibility of future price appreciation or continued principal paydown (Section 5), while foregoing the certainty of the sale-proceeds outcome shown in Section 4.

---

## Sources Cited

- U.S. Census Bureau, Quarterly Residential Vacancies and Homeownership report (Q1 2026), accessed July 2026.
- Freddie Mac Primary Mortgage Market Survey archive (August 2022 data), accessed July 2026.
- Apartments.com same-building condo listings (#106, #102, #310) and Maple Leaf neighborhood rent data, accessed July 2026.
- Redfin automated rent/value estimate and error-margin disclosure for 1740 NE 86th St #319, accessed July 2026.
- RentCafe average/median rent data for zip code 98115, accessed July 2026.
- IRS Publication 527, Residential Rental Property (2025 edition), accessed July 2026.
- IRS Publication 925, Passive Activity and At-Risk Rules (2025 edition), accessed July 2026.
- Washington Department of Revenue, "Rental vs. license to use real estate," accessed July 2026.
- Washington Department of Revenue, "Capital gains tax," accessed July 2026.
- Washington Department of Revenue REET rate schedule effective January 1, 2026, accessed July 2026.
- King County / MRSC, Real Estate Excise Tax local rate information, accessed July 2026.
- SB 6136 (Washington, 2023-24 session) bill summary, wa-law.org, accessed July 2026.
- Seattle housing/condo market reports (April and June 2026 data), accessed July 2026.
- John L Scott Ballard and Zillow same-building sale listings (#308, #301), accessed July 2026.
- Clever Real Estate / HomeLight 2026 real estate commission surveys, accessed July 2026.
- ClearLead Digital and AllPropertyManagement.com 2026 property management fee surveys, accessed July 2026.
