# Combined Affordability Assessment: Portland Home Purchase, Child-Rearing Costs, and the Seattle Condo

Prepared for Kate and Lucas. This document takes the home-purchase cost mechanics from `03-home-affordability/analysis.md`, the child-rearing cost projections from `02-future-budget/analysis.md`, and the Seattle condo carrying cost from `05-seattle-condo-decision/analysis.md` as fixed, given inputs. It does not recompute any of those figures. Its job is narrower: apply standard, published home affordability rules of thumb to the $600,000-$800,000 price range using those inputs, then cross-check the rules of thumb against a combined monthly cash flow that includes child-rearing costs and the condo, which the rules of thumb do not account for on their own. All arithmetic was computed in a Python script and checked before being placed in these tables. Figures are stated neutrally; this document does not recommend a price point or a course of action.

---

## 1. Inputs and Dependency Chain

Every dollar figure used below is pulled from one of the three source documents or from `shared/assumptions.md`. This section states exactly where each one comes from so the calculations that follow are traceable back to their origin.

**From `shared/assumptions.md`:**
- Combined gross annual household income: $308,520/year (Kate $165,000 + Lucas $143,520).
- Down payment: $200,000 (actual dollars), held separately from the $70,000 emergency fund.
- Other debts: none significant (no student loans or car payments affecting DTI), stated separately from the Seattle condo's existing mortgage, which is addressed on its own below.

**From `03-home-affordability/analysis.md`:**
- Section 1: net (after-tax) monthly income by scenario, at the "Partial" (6% of gross) retirement-contribution level, used as the primary income figures in this document (the "Max" and "Minimal" levels are not carried forward here; see Section 1 of that document for those figures):
  - Both working, current salaries: **$16,182/month**
  - Kate's income only (Lucas's lost): **$9,466/month**
  - Lucas's income only (Kate's lost): **$8,438/month**
- Section 2: all-in monthly housing cost by price point, base mortgage rate 6.55% (Freddie Mac PMMS, week ending July 16, 2026), and the itemized P&I / property tax / insurance components used to build a PITI-only figure for the rules of thumb in Section 2 below.
- Section 2: closing costs and the resulting emergency fund balance after closing costs are paid from the $70,000 fund.
- Section 3: all-in monthly housing cost at the base rate and at two mortgage-rate stress scenarios (+100 bps / 7.55%, +200 bps / 8.55%).

**From `02-future-budget/analysis.md`:**
- Section 4: baseline (non-housing, non-childcare) household living expenses, 0 children: **$3,000/month** in 2026 dollars, stated as applying to the household regardless of child count.
- Section 7 (primary reference table): monthly child-attributable cost (childcare + children's health insurance premium + the baseline-living increase attributable to children), by phase, in both today's (2026) dollars and inflation-projected nominal dollars:
  - Phase 1 (one child, infant, calendar years 2027-2028): today's $2,300/month; nominal $2,395/month at the start of the phase (2027), $2,495/month at the end (2028).
  - Phase 2 (two children, peak overlap, one infant plus one preschooler, calendar years 2029-2030): today's $3,900/month; nominal $4,405/month at the start of the phase (2029), $4,587/month at the end (2030).
- This document uses Phase 1 as the "1 child" figure and Phase 2 as the "2 children" figure, consistent with 02's own phase structure (Phase 1 is, by construction, the period when only one child exists).

**From `05-seattle-condo-decision/analysis.md`:**
- Section 1: condo carrying cost, base case (the given baseline figure, not the document's separate plausibility-check estimate): PITI $2,017 + HOA $435 + maintenance reserve $283 = **$2,735/month**. This is the raw carrying cost of owning the unit, independent of whether it is rented; it is used here as a fixed monthly outflow, per this document's scope, without re-litigating whether the condo should be kept or sold. Section 2 of that document additionally shows net cash flow if rented (in the "Base" rental scenario, $2,000/month asking rent, professionally managed: -$1,066/month net outflow after vacancy and management fee, i.e., a smaller net outflow than the raw $2,735 because rental income partially offsets it). This document uses the more conservative $2,735 raw carrying cost as the baseline figure throughout, since it does not depend on assuming any particular rental scenario or management arrangement.

**A note on a cost this document adds that the other two do not, and why:** `shared/known-modeling-issues.md` (issue 1) states that any surplus/deficit figure must net out adult baseline living expenses (~$3,000-$3,500/month), not just child-attributable costs and housing. `02-future-budget/analysis.md` explicitly excludes the $3,000/month adult baseline from its own child-cost totals because that cost applies regardless of child count and is "not a child-rearing cost" from that document's point of view. But for the combined cash flow check in Section 3 below to be a true full-picture number rather than a partial one, the $3,000/month base must still be included as its own line, on top of the child-attributable figures pulled from 02. Section 3 does this explicitly. Where a nominal (inflation-projected) figure for this $3,000 base is needed for a future calendar year, this document projects it forward using the same 3.0%/year general-inflation assumption stated in 02's Section 5, since 02 itself did not project this line forward (it was out of that document's scope). This is a modeling extension performed in this document, not a figure taken directly from 02, and is flagged as such.

---

## 2. Standard Home Affordability Rules of Thumb

### Rule definitions

- **28/36 rule.** The front-end ratio is the percentage of gross (pre-tax) monthly household income spent on housing costs, defined as principal, interest, property tax, homeowners insurance, and HOA/condo dues if any (commonly abbreviated PITI, or PITIA when dues are included). The guideline caps this at 28%. The back-end ratio (also called the debt-to-income ratio, or DTI) adds all other monthly debt obligations to the housing cost and caps the total at 36% of gross monthly income. This is a conventional mortgage-underwriting guideline, not a legal requirement; many lenders allow a DTI up to 45% on conventional loans (Bankrate, "What is the 28/36 rule for home affordability?", published June 2, 2026: https://www.bankrate.com/mortgages/what-is-the-28-36-rule/).
- **25%-of-take-home-pay rule.** A more conservative guideline, commonly associated with consumer-finance educator Dave Ramsey / Ramsey Solutions, stating that total monthly housing payment (again PITI, including PMI and HOA fees where applicable) should not exceed 25% of net (after-tax, take-home) monthly income (Ramsey Solutions, "How Much House Can I Afford?": https://www.ramseysolutions.com/real-estate/how-much-house-can-i-afford). This rule uses take-home pay rather than gross pay and a lower percentage than the 28/36 rule's front-end threshold, making it a stricter test.
- **Price-to-income multiplier.** A widely cited rule of thumb holds that home price should not exceed roughly 2.5 to 4 times gross annual household income, with the specific ceiling depending on the household's other debt load: sources describing this rule commonly present a "2.5x" ceiling as the most conservative version and describe less conservative ceilings (3x, 4x, up to 5x for a debt-free buyer) as appropriate only as existing debt decreases (HomeLight, "10 Rules of Thumb to Determine How Much House You Can Afford," published June 24, 2026: https://www.homelight.com/blog/buyer-how-much-house-can-i-afford-rule-of-thumb/). This document tests both the conservative 2.5x ceiling and the more permissive 4x ceiling explicitly, since the household carries no other consumer debt (per `shared/assumptions.md`).

### Method

- Gross monthly household income = $308,520 / 12 = $25,710/month.
- PITI-only monthly cost at each price point is built from the itemized components in `03-home-affordability/analysis.md` Section 2 (P&I + property tax + insurance; there is no HOA on the Portland property itself). This is narrower than that document's "all-in" total, which also includes a maintenance reserve and utilities; those two items are excluded here because they fall outside the standard PITI definition used by both the 28/36 rule and the 25%-of-net rule.
- Front-end ratio = PITI-only / gross monthly income. Back-end ratio, in the base version below, equals the front-end ratio because `shared/assumptions.md` states there is no other significant consumer debt.
- A supplementary back-end variant also accounts for the Seattle condo's existing mortgage obligation, since it is a real, ongoing debt the household carries even though `shared/assumptions.md`'s "no other significant debt" language is describing consumer debt (student loans, car payments), not the existing investment property mortgage. Fannie Mae's rental income guidance (Fannie Mae Selling Guide, B3-3.1-08, "Rental Income": https://selling-guide.fanniemae.com/sel/b3-3.8-01/rental-income) provides that for a non-owner-occupied rental property, qualifying rental income (typically 75% of documented gross rent) is netted against the property's full PITIA; if the result is negative, the shortfall is added to the borrower's monthly debt for DTI purposes. Using the condo's PITI + HOA ($2,017 + $435 = $2,452/month, `05-seattle-condo-decision/analysis.md` Section 1) against 75% of the "Base" rental scenario rent ($2,000/month, `05-seattle-condo-decision/analysis.md` Section 2, i.e., $1,500/month qualifying income), the shortfall is $2,452 - $1,500 = $952/month, which this variant adds to the back-end ratio. A separate, more conservative variant assumes no documented rental income is available to the lender at all (for example, no qualifying lease history) and counts the condo's full $2,452 PITI + HOA as debt.
- Price-to-income multiplier = price / $308,520.

### Results by price point

| Price | PITI-only | Front-end ratio | 28% pass? | Back-end ratio (no other debt) | 36% pass? | Back-end w/ condo (Fannie Mae rental offset, Base scenario) | 36% pass? | Back-end w/ condo (full PITIA, no rental credit) | 36% pass? | 25%-of-net ratio (both working) | 25% pass? | Price / gross income | <=2.5x? | <=4.0x? |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| $600,000 | $3,270 | 12.7% | Yes | 12.7% | Yes | 16.4% | Yes | 22.3% | Yes | 20.2% | Yes | 1.94x | Yes | Yes |
| $650,000 | $3,645 | 14.2% | Yes | 14.2% | Yes | 17.9% | Yes | 23.7% | Yes | 22.5% | Yes | 2.11x | Yes | Yes |
| $700,000 | $4,019 | 15.6% | Yes | 15.6% | Yes | 19.3% | Yes | 25.2% | Yes | 24.8% | Yes | 2.27x | Yes | Yes |
| $750,000 | $4,394 | 17.1% | Yes | 17.1% | Yes | 20.8% | Yes | 26.6% | Yes | 27.2% | No | 2.43x | Yes | Yes |
| $800,000 | $4,769 | 18.5% | Yes | 18.5% | Yes | 22.3% | Yes | 28.1% | Yes | 29.5% | No | 2.59x | No | Yes |

- By the 28/36 rule, every price point in the $600,000-$800,000 range passes both the front-end and back-end thresholds by a wide margin, whether or not the Seattle condo's mortgage is counted as debt.
- By the 25%-of-net rule, $600,000-$700,000 pass; $750,000 (27.2%) and $800,000 (29.5%) fail.
- By the price-to-income multiplier, all five price points pass the more permissive 4.0x ceiling; only $800,000 (2.59x) exceeds the more conservative 2.5x ceiling.

---

## 3. Combined Cash Flow Reality Check

### Method

- Monthly surplus/deficit = net monthly income (03, Section 1) minus all-in monthly housing cost (03, Section 2, base 6.55% rate) minus the Seattle condo carrying cost ($2,735/month, 05, Section 1) minus the full monthly non-housing household living cost.
- Full monthly non-housing household living cost = the $3,000/month adult baseline (02, Section 4) plus the child-attributable cost for the relevant scenario (02, Section 7): $0 for 0 children, $2,300/month (today's dollars, Phase 1) for 1 child, $3,900/month (today's dollars, Phase 2) for 2 children at peak overlap.
- Three versions are shown: today's (2026) dollars; nominal dollars at the start of the relevant phase (2027 for 1 child, 2029 for 2 children); and nominal dollars at the end of the relevant phase (2028 for 1 child, 2030 for 2 children). The nominal versions inflate the child-attributable cost using 02's own stated rates (4.5%/year childcare, 3.0%/year health premium and baseline-living increase) and inflate the $3,000 adult baseline using the same 3.0%/year general-inflation assumption (this last step is this document's own extension of 02's method, as noted in Section 1 above). The mortgage payment itself is fixed-rate and does not change with these projections; the condo carrying cost is also held flat here, since 05 does not model condo cost inflation.
- The base-case income figure is "both working, Partial retirement level" ($16,182/month, 03 Section 1). The single-income scenarios (Kate's income only, Lucas's income only, both Partial level) are shown separately, in today's dollars only, for contrast.

### Base case (both working): today's dollars

| Price | 0 children | 1 child (Phase 1, infant) | 2 children (Phase 2, peak overlap) |
|---|---|---|---|
| $600,000 | $6,377 | $4,077 | $2,477 |
| $650,000 | $5,961 | $3,661 | $2,061 |
| $700,000 | $5,544 | $3,244 | $1,644 |
| $750,000 | $5,128 | $2,828 | $1,228 |
| $800,000 | $4,711 | $2,411 | $811 |

### Base case (both working): nominal dollars, start of relevant phase (2027 for 1 child, 2029 for 2 children)

| Price | 0 children | 1 child | 2 children |
|---|---|---|---|
| $600,000 | $6,377 | $3,892 | $1,694 |
| $650,000 | $5,961 | $3,476 | $1,278 |
| $700,000 | $5,544 | $3,059 | $861 |
| $750,000 | $5,128 | $2,643 | $445 |
| $800,000 | $4,711 | $2,226 | $28 |

### Base case (both working): nominal dollars, end of relevant phase (2028 for 1 child, 2030 for 2 children)

| Price | 0 children | 1 child | 2 children |
|---|---|---|---|
| $600,000 | $6,377 | $3,699 | $1,413 |
| $650,000 | $5,961 | $3,283 | $997 |
| $700,000 | $5,544 | $2,866 | $580 |
| $750,000 | $5,128 | $2,450 | $164 |
| $800,000 | $4,711 | $2,033 | -$253 |

### Single-income scenarios, for contrast (today's dollars)

| Price | Kate's income only, 0 kids | Kate's income only, 1 child | Kate's income only, 2 children | Lucas's income only, 0 kids | Lucas's income only, 1 child | Lucas's income only, 2 children |
|---|---|---|---|---|---|---|
| $600,000 | -$339 | -$2,639 | -$4,239 | -$1,367 | -$3,667 | -$5,267 |
| $650,000 | -$755 | -$3,055 | -$4,655 | -$1,783 | -$4,083 | -$5,683 |
| $700,000 | -$1,172 | -$3,472 | -$5,072 | -$2,200 | -$4,500 | -$6,100 |
| $750,000 | -$1,588 | -$3,888 | -$5,488 | -$2,616 | -$4,916 | -$6,516 |
| $800,000 | -$2,005 | -$4,305 | -$5,905 | -$3,033 | -$5,333 | -$6,933 |

- In every single-income scenario shown, at every price point and every child count including 0 children, monthly cash flow is negative once the Seattle condo carrying cost and full living expenses are included. The single-income deficit exists even before any child-rearing cost is added.
- In the both-working base case, the combined monthly figure is positive at every price point and child count in today's dollars, but turns negative at $800,000 with 2 children by the end of the peak-overlap phase in nominal dollars (-$253/month), and is close to zero at $750,000 in that same nominal end-of-phase column ($164/month).

---

## 4. Where the Rules of Thumb and the Full Cash-Flow Picture Diverge

- At every price point from $600,000 to $800,000, the 28/36 rule shows a comfortable pass on both the front-end and back-end ratios (front-end ranges from 12.7% to 18.5%, well under the 28% threshold; back-end ratios, even in the most conservative variant that fully counts the Seattle condo's mortgage as debt with no rental-income credit, range from 22.3% to 28.1%, still under 36%). The 28/36 rule does not register a problem anywhere in this price range.
- The 25%-of-net rule diverges starting at $750,000 (27.2%, a fail) and $800,000 (29.5%, a fail), while $600,000-$700,000 pass. This rule fails at the top two price points using housing cost alone, before any child-rearing or condo cost is added.
- The price-to-income multiplier is within the more permissive 4.0x ceiling at every price point, and within the more conservative 2.5x ceiling everywhere except $800,000 (2.59x).
- None of the three rules of thumb incorporate child-rearing costs or a second property's carrying cost, since none of them are designed to. The combined cash-flow check in Section 3 shows where that omission matters most:
  - With 0 children, the base-case (both-working) combined cash flow is positive by $4,711 to $6,377/month across the full price range, consistent with the front-end and back-end ratios both showing wide margins.
  - With 1 child, the combined cash flow is still positive at every price point in today's dollars ($2,411 to $4,077/month) and in nominal dollars at the start and end of Phase 1.
  - With 2 children at peak overlap, the combined cash-flow picture narrows substantially and, at the two highest price points, crosses into a range the 28/36 and price-to-income rules do not flag at all: today's-dollars surplus is $811-$2,477/month across the range, but by the nominal end of the peak-overlap phase (2030), $800,000 shows a monthly deficit (-$253) and $750,000 shows a narrow surplus ($164/month), while $600,000-$700,000 remain positive ($580-$1,413/month).
  - The 25%-of-net rule is the only one of the three rules of thumb that also flags $750,000 and $800,000 as exceeding its threshold, but it does so using housing cost alone, without reference to children or the condo; the direction of its signal (higher price points are tighter) agrees with the combined cash-flow check's direction, even though the two are not calculating the same thing.
  - The 28/36 rule and the price-to-income multiplier (at its 4.0x ceiling) do not flag any price point in this range, including the combinations where the combined cash-flow check shows a narrow or negative monthly result.
- In the single-income scenarios, the divergence is present at every price point and every child count, including 0 children: the rules of thumb in Section 2 are calculated only against the both-working base case (03's Section 1 does not restate them for the single-income scenarios), so there is no direct single-income rule-of-thumb figure to compare against. The combined cash-flow check shows single-income deficits at every combination shown, which is a divergence from the implicit assumption, built into affordability rules of thumb generally, that the qualifying income is stable and continues unchanged.

---

## 5. Emergency Fund Runway Under Income-Loss Scenarios

### Method

- Starting balance: the $70,000 emergency fund after closing costs are paid from it (03, Section 2), which varies by price point because closing costs scale with price.
- Monthly net cash flow in each income-loss scenario = net monthly income (03, Section 1, single-income Partial level) minus all-in monthly housing cost (03, Section 2, base rate) minus the condo carrying cost ($2,735/month, 05, Section 1) minus full monthly living cost (02, Sections 4 and 7, today's dollars).
- Runway in months = starting emergency fund balance / absolute value of the monthly deficit, shown only where the monthly figure is negative (in every scenario modeled here, it is negative).
- Two child-count scenarios are shown: 0 children (income loss occurring before children arrive) and 2 children at peak overlap (income loss occurring during the highest-cost child-rearing phase). The 1-child case falls between these two and is not tabulated separately here.

### Kate's income only (Lucas's income lost), 0 children

| Price | EF after closing | Monthly net | Runway (months) |
|---|---|---|---|
| $600,000 | $54,701 | -$339 | 161.4 |
| $650,000 | $53,352 | -$755 | 70.7 |
| $700,000 | $52,002 | -$1,172 | 44.4 |
| $750,000 | $50,653 | -$1,588 | 31.9 |
| $800,000 | $49,304 | -$2,005 | 24.6 |

### Kate's income only (Lucas's income lost), 2 children at peak overlap

| Price | EF after closing | Monthly net | Runway (months) |
|---|---|---|---|
| $600,000 | $54,701 | -$4,239 | 12.9 |
| $650,000 | $53,352 | -$4,655 | 11.5 |
| $700,000 | $52,002 | -$5,072 | 10.3 |
| $750,000 | $50,653 | -$5,488 | 9.2 |
| $800,000 | $49,304 | -$5,905 | 8.3 |

### Lucas's income only (Kate's income lost), 0 children

| Price | EF after closing | Monthly net | Runway (months) |
|---|---|---|---|
| $600,000 | $54,701 | -$1,367 | 40.0 |
| $650,000 | $53,352 | -$1,783 | 29.9 |
| $700,000 | $52,002 | -$2,200 | 23.6 |
| $750,000 | $50,653 | -$2,616 | 19.4 |
| $800,000 | $49,304 | -$3,033 | 16.3 |

### Lucas's income only (Kate's income lost), 2 children at peak overlap

| Price | EF after closing | Monthly net | Runway (months) |
|---|---|---|---|
| $600,000 | $54,701 | -$5,267 | 10.4 |
| $650,000 | $53,352 | -$5,683 | 9.4 |
| $700,000 | $52,002 | -$6,100 | 8.5 |
| $750,000 | $50,653 | -$6,516 | 7.8 |
| $800,000 | $49,304 | -$6,933 | 7.1 |

- In every income-loss scenario modeled, monthly cash flow is negative even with 0 children, because the combination of housing cost and the condo carrying cost exceeds a single income at every price point tested.
- Runway is highest for the 0-children, Kate's-income-only scenario at the lowest price point (161.4 months) and lowest for the 2-children, Lucas's-income-only scenario at the highest price point (7.1 months).
- These figures assume unchanged spending during the income-loss period (no reduction in discretionary costs); per `shared/known-modeling-issues.md` (issue 16), a scenario that allows for spending cuts during a shortfall would show a longer runway than the figures above.

---

## 6. Mortgage Rate Sensitivity on the Combined Picture

### Method

- Uses the both-working base-case net income ($16,182/month), the condo carrying cost ($2,735/month), and the 2-children peak-overlap living cost in today's dollars ($3,000 + $3,900 = $6,900/month).
- All-in monthly housing cost at each price point and rate comes from `03-home-affordability/analysis.md` Section 3: base rate 6.55%, +100 basis points (7.55%), +200 basis points (8.55%).

| Price | Combined surplus/deficit @ 6.55% | Combined surplus/deficit @ 7.55% | Combined surplus/deficit @ 8.55% |
|---|---|---|---|
| $600,000 | $2,477 | $2,207 | $1,928 |
| $650,000 | $2,061 | $1,758 | $1,444 |
| $700,000 | $1,644 | $1,308 | $959 |
| $750,000 | $1,228 | $857 | $473 |
| $800,000 | $811 | $407 | -$12 |

- At $800,000, a 200 basis point rate increase (from 6.55% to 8.55%) moves the combined monthly figure from a $811 surplus to a $12 deficit, in today's dollars, before accounting for any nominal cost escalation over the child-rearing years shown in Section 3.
- At every other price point shown, the combined figure remains positive across the full rate-stress range, though the margin narrows at each step: $750,000 falls from $1,228 to $473; $700,000 falls from $1,644 to $959.

---

## Sources

- `shared/assumptions.md` (combined gross income, down payment, emergency fund, other-debt statement).
- `shared/known-modeling-issues.md`, issue 1 (baseline living expenses must be netted from any surplus figure) and issue 16 (emergency fund runway should note whether it assumes unchanged spending).
- `02-future-budget/analysis.md`, Sections 4 and 7 (baseline living expenses, child-attributable costs by phase, today's dollars and nominal dollars).
- `03-home-affordability/analysis.md`, Sections 1, 2, and 3 (net monthly income by scenario, all-in monthly housing cost by price point, closing costs and post-closing emergency fund balance, mortgage rate sensitivity).
- `05-seattle-condo-decision/analysis.md`, Sections 1 and 2 (condo carrying cost baseline, rental scenario rents).
- Bankrate, "What is the 28/36 rule for home affordability?", published June 2, 2026: https://www.bankrate.com/mortgages/what-is-the-28-36-rule/
- Ramsey Solutions, "How Much House Can I Afford?": https://www.ramseysolutions.com/real-estate/how-much-house-can-i-afford
- HomeLight, "10 Rules of Thumb to Determine How Much House You Can Afford," published June 24, 2026: https://www.homelight.com/blog/buyer-how-much-house-can-i-afford-rule-of-thumb/
- Fannie Mae Selling Guide, B3-3.1-08, "Rental Income": https://selling-guide.fanniemae.com/sel/b3-3.8-01/rental-income

## Method Notes Addressed From Known Modeling Issues

This document addresses issue 1 from `shared/known-modeling-issues.md` directly: the combined cash-flow figures in Sections 3, 5, and 6 net out the $3,000/month adult baseline living cost in addition to child-attributable costs and housing, rather than presenting a surplus that omits it. It also addresses issue 16 by stating explicitly that the emergency fund runway figures in Section 5 assume unchanged spending during an income-loss period, not a reduced-spending scenario. Every dollar figure describing housing cost, child-rearing cost, and condo carrying cost is cited to a specific section of `02-future-budget/analysis.md`, `03-home-affordability/analysis.md`, or `05-seattle-condo-decision/analysis.md` per this document's stated purpose of making the dependency chain auditable. Prose throughout states what the numbers show without advice-toned framing, consistent with the tone requirement in `shared/assumptions.md`.
