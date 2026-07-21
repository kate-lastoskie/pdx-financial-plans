# Combined Affordability Assessment: Portland Home Purchase, Child-Rearing Costs, and the Seattle Condo

Prepared for Kate and Lucas. This document takes the home-purchase cost mechanics from `03-home-affordability/README.md`, the child-rearing cost projections from `02-future-budget/README.md` (Part 2, Child Budget), and the Seattle condo carrying cost from `05-seattle-condo-decision/README.md` as fixed, given inputs. It does not recompute any of those figures. Its job is narrower: apply standard, published home affordability rules of thumb to the $600,000-$800,000 price range using those inputs, then cross-check the rules of thumb against a combined monthly cash flow that includes child-rearing costs and the condo, which the rules of thumb do not account for on their own. All arithmetic was computed in a Python script and checked before being placed in these tables. Figures are stated neutrally; this document does not recommend a price point or a course of action.

---

## 1. Inputs and Dependency Chain

Every dollar figure used below is pulled from one of the source documents or from `shared/assumptions.md`. This section states exactly where each one comes from so the calculations that follow are traceable back to their origin.

**From `shared/assumptions.md`:**
- Combined gross annual household income: $308,520/year (Kate $165,000 + Lucas $143,520).
- Down payment: $200,000 (actual dollars), held separately from the $70,000 emergency fund.
- Other debts: none significant (no student loans or car payments affecting DTI), stated separately from the Seattle condo's existing mortgage, which is addressed on its own below.

**From `03-home-affordability/README.md`:**
- Section 1: net (after-tax) monthly income by scenario, at the "Partial" (6% of gross) retirement-contribution level, used as the primary income figures in this document (the "Max" and "Minimal" levels are not carried forward here; see Section 1 of that document for those figures):
  - Both working, current salaries: **$16,182/month**
  - Kate's income only (Lucas's lost): **$9,466/month**
  - Lucas's income only (Kate's lost): **$8,438/month**
- Section 2: all-in monthly housing cost by price point, base mortgage rate 6.55% (Freddie Mac PMMS, week ending July 16, 2026), and the itemized P&I / property tax / insurance components used to build a PITI-only figure for the rules of thumb in Section 2 below.
- Section 2: closing costs and the resulting emergency fund balance after closing costs are paid from the $70,000 fund.
- Section 3: all-in monthly housing cost at the base rate and at two mortgage-rate stress scenarios (+100 bps / 7.55%, +200 bps / 8.55%).

**From `02-future-budget/README.md`, Part 2 (Child Budget) (supersedes the deleted, earlier `02-future-budget/analysis.md`):**

This document now models eight phases across an 18-year window (2027-2044, Child A birth through age 17), rather than the prior five-phase, 12-year model, and adds food, clothing, entertainment/activities, camps, youth sports, and a child-specific vacation increment on top of the childcare and health-premium figures the prior version had. Section 10 of Part 2 (Child Budget) ("Monthly Child-Attributable Cost by Phase") is its primary reference table and is reproduced here in full so every phase, not just the two used in the calculations below, is visible:

| Phase | Years | Description | Total, today's $/mo (2026), start of phase | Total, today's $/mo, end of phase (Section 9) | Total, nominal $/mo, start of phase | Total, nominal $/mo, end of phase (Section 9) |
|---|---|---|---|---|---|---|
| 1 | 2027-2028 | Child A infant only | $2,613 | $2,613 | $2,717 | $2,826 |
| 2 | 2029-2030 | Peak overlap (infant + preschool) | $4,526 | $4,576 | $5,088 | $5,348 |
| 3 | 2031 | Both preschool | $4,026 | $4,026 | $4,876 | $4,876 |
| 4 | 2032-2033 | School-age aftercare + preschool | $4,072 | $4,163 | $5,074 | $5,375 |
| 5 | 2034-2038 | Both elementary school-age | $4,158 | $4,463 | $5,500 | $6,769 |
| 6 | 2039-2040 | Middle school + late elementary | $3,710 | $3,710 | $5,675 | $5,866 |
| 7 | 2041-2042 | Early high school + middle school | $2,716 | $2,729 | $4,231 | $4,379 |
| 8 | 2043-2044 | Later high school + high school | $2,489 | $2,502 | $4,114 | $4,259 |

- This document uses **Phase 1** as the "1 child" figure and **Phase 2** as the "2 children, peak overlap" figure in Sections 3, 5, and 6 below, consistent with the prior version's structure (Phase 1 is, by construction, the period when only one child exists, and Phase 2 is the highest today's-dollars phase). The fuller 8-phase, 18-year table above is available if a reader wants the picture at other ages: for example, Phases 5-8 now have real, modeled costs for the elementary, middle-school, and teen years, which the prior 12-year version of `02-future-budget/analysis.md` (since removed) did not cover at all past age 12 (in fact Phases 5-8, evaluated in nominal dollars, exceed Phase 2's nominal figure by the time they occur, since inflation has compounded for longer even though the today's-dollars figure is lower; see Part 2, Child Budget, Section 9).
- Phase totals combine childcare/aftercare (Part 2, Child Budget, Section 2), children's health insurance premium (Section 3), food (Section 4), clothing (Section 5), and entertainment/activities (Section 6, plus camps/sports/vacation increment from Section 7 where applicable to that phase's ages). Inflation assumptions (childcare at 4.5%/year, all other categories at 3.0%/year general inflation) are documented in Section 8 of Part 2 (Child Budget).
- Per Part 2 (Child Budget) Section 11 ("What This Document Does Not Cover"), it explicitly excludes housing/mortgage costs, the Seattle condo carrying cost, and adult/household-level baseline living expenses and the adults' own vacation budget; those remain the scope of `03-home-affordability/README.md`, `05-seattle-condo-decision/README.md`, and `02-future-budget/README.md` (Part 1, Adult Budget) respectively, as before.

**From `02-future-budget/README.md`, Part 1 (Adult Budget):**

Part 1 (Adult Budget) is an intentionally blank fillable template for Kate and Lucas's adult-only household costs (groceries, adult entertainment, family vacation base cost, and similar categories); it contains no populated dollar figures. The prior version of this document sourced its $3,000/month adult baseline living estimate from the old, now-removed `02-future-budget/analysis.md` Section 4. That line item no longer lives in a research-backed document. Rather than attribute it to a source that no longer contains it, this document now states it as its own placeholder:

> This document uses a placeholder adult baseline living estimate of $3,000/month (2026 dollars, 0-children basis), carried forward from an earlier version of this analysis, because Part 1 (Adult Budget) is an intentionally blank template for Kate and Lucas to fill in with real numbers. Once that template is filled in, the figures in this section should be recalculated using the actual adult budget instead of this placeholder.

**From `05-seattle-condo-decision/README.md`:**
- Section 1: condo carrying cost, base case (the given baseline figure, not the document's separate plausibility-check estimate): PITI $2,017 + HOA $435 + maintenance reserve $283 = **$2,735/month**. This is the raw carrying cost of owning the unit, independent of whether it is rented; it is used here as a fixed monthly outflow, per this document's scope, without re-litigating whether the condo should be kept or sold. Section 2 of that document additionally shows net cash flow if rented (in the "Base" rental scenario, $2,000/month asking rent, professionally managed: -$1,066/month net outflow after vacancy and management fee, i.e., a smaller net outflow than the raw $2,735 because rental income partially offsets it). This document uses the more conservative $2,735 raw carrying cost as the baseline figure throughout, since it does not depend on assuming any particular rental scenario or management arrangement.

**A note on why this document carries the $3,000/month adult baseline as its own explicit assumption:** `shared/known-modeling-issues.md` (issue 1) states that any surplus/deficit figure must net out adult baseline living expenses (~$3,000-$3,500/month), not just child-attributable costs and housing. `02-future-budget/README.md` (Part 2, Child Budget) explicitly excludes any adult baseline from its own child-cost totals (Section 11); that line now belongs to Part 1 (Adult Budget), which is intentionally blank. For the combined cash flow check in Section 3 below to be a true full-picture number rather than a partial one, the $3,000/month placeholder must still be included as its own line, on top of the child-attributable figures pulled from Part 2 (Child Budget). Section 3 does this explicitly. Where a nominal (inflation-projected) figure for this $3,000 placeholder is needed for a future calendar year, this document projects it forward using the same 3.0%/year general-inflation assumption stated in Part 2 (Child Budget) Section 8, since neither Part 2 (Child Budget) nor the blank Part 1 (Adult Budget) projects this line forward. This is a modeling extension performed in this document, not a figure taken directly from either source, and is flagged as such, consistent with how the prior version of this document handled the same extension.

---

## 2. Standard Home Affordability Rules of Thumb

### Rule definitions

- **28/36 rule.** The front-end ratio is the percentage of gross (pre-tax) monthly household income spent on housing costs, defined as principal, interest, property tax, homeowners insurance, and HOA/condo dues if any (commonly abbreviated PITI, or PITIA when dues are included). The guideline caps this at 28%. The back-end ratio (also called the debt-to-income ratio, or DTI) adds all other monthly debt obligations to the housing cost and caps the total at 36% of gross monthly income. This is a conventional mortgage-underwriting guideline, not a legal requirement; many lenders allow a DTI up to 45% on conventional loans (Bankrate, "What is the 28/36 rule for home affordability?", published June 2, 2026: https://www.bankrate.com/mortgages/what-is-the-28-36-rule/).
- **25%-of-take-home-pay rule.** A more conservative guideline, commonly associated with consumer-finance educator Dave Ramsey / Ramsey Solutions, stating that total monthly housing payment (again PITI, including PMI and HOA fees where applicable) should not exceed 25% of net (after-tax, take-home) monthly income (Ramsey Solutions, "How Much House Can I Afford?": https://www.ramseysolutions.com/real-estate/how-much-house-can-i-afford). This rule uses take-home pay rather than gross pay and a lower percentage than the 28/36 rule's front-end threshold, making it a stricter test.
- **Price-to-income multiplier.** A widely cited rule of thumb holds that home price should not exceed roughly 2.5 to 4 times gross annual household income, with the specific ceiling depending on the household's other debt load: sources describing this rule commonly present a "2.5x" ceiling as the most conservative version and describe less conservative ceilings (3x, 4x, up to 5x for a debt-free buyer) as appropriate only as existing debt decreases (HomeLight, "10 Rules of Thumb to Determine How Much House You Can Afford," published June 24, 2026: https://www.homelight.com/blog/buyer-how-much-house-can-i-afford-rule-of-thumb/). This document tests both the conservative 2.5x ceiling and the more permissive 4x ceiling explicitly, since the household carries no other consumer debt (per `shared/assumptions.md`).

### Method

- Gross monthly household income = $308,520 / 12 = $25,710/month.
- PITI-only monthly cost at each price point is built from the itemized components in `03-home-affordability/README.md` Section 2 (P&I + property tax + insurance; there is no HOA on the Portland property itself). This is narrower than that document's "all-in" total, which also includes a maintenance reserve and utilities; those two items are excluded here because they fall outside the standard PITI definition used by both the 28/36 rule and the 25%-of-net rule.
- Front-end ratio = PITI-only / gross monthly income. Back-end ratio, in the base version below, equals the front-end ratio because `shared/assumptions.md` states there is no other significant consumer debt.
- A supplementary back-end variant also accounts for the Seattle condo's existing mortgage obligation, since it is a real, ongoing debt the household carries even though `shared/assumptions.md`'s "no other significant debt" language is describing consumer debt (student loans, car payments), not the existing investment property mortgage. Fannie Mae's rental income guidance (Fannie Mae Selling Guide, B3-3.1-08, "Rental Income": https://selling-guide.fanniemae.com/sel/b3-3.8-01/rental-income) provides that for a non-owner-occupied rental property, qualifying rental income (typically 75% of documented gross rent) is netted against the property's full PITIA; if the result is negative, the shortfall is added to the borrower's monthly debt for DTI purposes. Using the condo's PITI + HOA ($2,017 + $435 = $2,452/month, `05-seattle-condo-decision/README.md` Section 1) against 75% of the "Base" rental scenario rent ($2,000/month, `05-seattle-condo-decision/README.md` Section 2, i.e., $1,500/month qualifying income), the shortfall is $2,452 - $1,500 = $952/month, which this variant adds to the back-end ratio. A separate, more conservative variant assumes no documented rental income is available to the lender at all (for example, no qualifying lease history) and counts the condo's full $2,452 PITI + HOA as debt.
- Price-to-income multiplier = price / $308,520.
- None of these ratios or thresholds involve child-rearing costs, so this section's figures are unchanged by the Part 2 (Child Budget) update; they are reproduced here for completeness and cross-checked, not recalculated with new inputs.

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
- Full monthly non-housing household living cost = the $3,000/month adult baseline placeholder (this document, Section 1) plus the child-attributable cost for the relevant scenario (Part 2, Child Budget, Section 10): $0 for 0 children, $2,613/month (today's dollars, Phase 1) for 1 child, $4,526/month (today's dollars, Phase 2, start-of-phase figure; per Part 2 (Child Budget) Section 9 this rises to $4,576/month by the end of the phase) for 2 children at peak overlap.
- Three versions are shown: today's (2026) dollars; nominal dollars at the start of the relevant phase (2027 for 1 child, 2029 for 2 children); and nominal dollars at the end of the relevant phase (2028 for 1 child, 2030 for 2 children). The nominal versions inflate the child-attributable cost using Part 2's (Child Budget) own stated rates (4.5%/year childcare/aftercare; 3.0%/year for health premium, food, clothing, and entertainment/activities, per Part 2, Child Budget, Section 8) and inflate the $3,000 adult baseline placeholder using the same 3.0%/year general-inflation assumption (this last step is this document's own extension, as noted in Section 1 above, since neither Part 2 (Child Budget) nor Part 1 (Adult Budget) projects the adult baseline forward). The mortgage payment itself is fixed-rate and does not change with these projections; the condo carrying cost is also held flat here, since 05 does not model condo cost inflation.
- The base-case income figure is "both working, Partial retirement level" ($16,182/month, 03 Section 1). The single-income scenarios (Kate's income only, Lucas's income only, both Partial level) are shown separately, in today's dollars only, for contrast.

### Base case (both working): today's dollars

| Price | 0 children | 1 child (Phase 1, infant) | 2 children (Phase 2, peak overlap) |
|---|---|---|---|
| $600,000 | $6,377 | $3,764 | $1,851 |
| $650,000 | $5,961 | $3,348 | $1,435 |
| $700,000 | $5,544 | $2,931 | $1,018 |
| $750,000 | $5,128 | $2,515 | $602 |
| $800,000 | $4,711 | $2,098 | $185 |

### Base case (both working): nominal dollars, start of relevant phase (2027 for 1 child, 2029 for 2 children)

| Price | 0 children | 1 child | 2 children |
|---|---|---|---|
| $600,000 | $6,377 | $3,570 | $1,011 |
| $650,000 | $5,961 | $3,154 | $595 |
| $700,000 | $5,544 | $2,737 | $178 |
| $750,000 | $5,128 | $2,321 | -$238 |
| $800,000 | $4,711 | $1,904 | -$655 |

### Base case (both working): nominal dollars, end of relevant phase (2028 for 1 child, 2030 for 2 children)

| Price | 0 children | 1 child | 2 children |
|---|---|---|---|
| $600,000 | $6,377 | $3,368 | $652 |
| $650,000 | $5,961 | $2,952 | $236 |
| $700,000 | $5,544 | $2,535 | -$181 |
| $750,000 | $5,128 | $2,119 | -$597 |
| $800,000 | $4,711 | $1,702 | -$1,014 |

### Single-income scenarios, for contrast (today's dollars)

| Price | Kate's income only, 0 kids | Kate's income only, 1 child | Kate's income only, 2 children | Lucas's income only, 0 kids | Lucas's income only, 1 child | Lucas's income only, 2 children |
|---|---|---|---|---|---|---|
| $600,000 | -$339 | -$2,952 | -$4,865 | -$1,367 | -$3,980 | -$5,893 |
| $650,000 | -$755 | -$3,368 | -$5,281 | -$1,783 | -$4,396 | -$6,309 |
| $700,000 | -$1,172 | -$3,785 | -$5,698 | -$2,200 | -$4,813 | -$6,726 |
| $750,000 | -$1,588 | -$4,201 | -$6,114 | -$2,616 | -$5,229 | -$7,142 |
| $800,000 | -$2,005 | -$4,618 | -$6,531 | -$3,033 | -$5,646 | -$7,559 |

- In every single-income scenario shown, at every price point and every child count including 0 children, monthly cash flow is negative once the Seattle condo carrying cost and full living expenses are included. The single-income deficit exists even before any child-rearing cost is added.
- In the both-working base case, the combined monthly figure is positive at every price point and child count in today's dollars, though at $800,000 with 2 children it is only $185/month, a narrow margin even before any inflation is applied. In nominal dollars, 2-children figures turn negative starting at the start of the peak-overlap phase (2029) at $750,000 (-$238) and $800,000 (-$655), and by the end of that phase (2030) $700,000 also turns negative (-$181), leaving only $600,000 ($652) and $650,000 ($236) positive.

---

## 4. Where the Rules of Thumb and the Full Cash-Flow Picture Diverge

- At every price point from $600,000 to $800,000, the 28/36 rule shows a comfortable pass on both the front-end and back-end ratios (front-end ranges from 12.7% to 18.5%, well under the 28% threshold; back-end ratios, even in the most conservative variant that fully counts the Seattle condo's mortgage as debt with no rental-income credit, range from 22.3% to 28.1%, still under 36%). The 28/36 rule does not register a problem anywhere in this price range.
- The 25%-of-net rule diverges starting at $750,000 (27.2%, a fail) and $800,000 (29.5%, a fail), while $600,000-$700,000 pass. This rule fails at the top two price points using housing cost alone, before any child-rearing or condo cost is added.
- The price-to-income multiplier is within the more permissive 4.0x ceiling at every price point, and within the more conservative 2.5x ceiling everywhere except $800,000 (2.59x).
- None of the three rules of thumb incorporate child-rearing costs or a second property's carrying cost, since none of them are designed to. The combined cash-flow check in Section 3, now built on Part 2's (Child Budget) more detailed (and materially higher) phase figures, shows where that omission matters most:
  - With 0 children, the base-case (both-working) combined cash flow is positive by $4,711 to $6,377/month across the full price range, consistent with the front-end and back-end ratios both showing wide margins. This figure is unchanged from the prior version of this document, since it does not depend on child costs.
  - With 1 child, the combined cash flow is still positive at every price point in today's dollars ($2,098 to $3,764/month) and in nominal dollars at the start and end of Phase 1 ($1,702 to $3,570/month across both nominal tables), though these figures are lower than the prior version's ($2,411-$4,077/month today's dollars) because Phase 1's total now includes food, clothing, and entertainment costs the prior version's Phase 1 did not.
  - With 2 children at peak overlap, the combined cash-flow picture narrows substantially, more than it did in the prior version. Today's-dollars surplus is now $185-$1,851/month across the price range (versus $811-$2,477/month previously), and at $800,000 the today's-dollars margin has essentially collapsed to a token surplus. In nominal dollars, the crossover into negative territory now begins earlier and at more price points than before: by the **start** of the peak-overlap phase (2029), $750,000 and $800,000 are already negative (-$238 and -$655/month); by the **end** of the phase (2030), $700,000 joins them (-$181/month), leaving only $600,000 ($652) and $650,000 ($236) positive. The prior version of this document showed only $800,000 turning negative, and only at the end of the phase (-$253/month); the new, more detailed child-cost figures push that finding to a wider set of price points and an earlier point in time.
  - The 25%-of-net rule is the only one of the three rules of thumb that also flags $750,000 and $800,000 as exceeding its threshold, but it does so using housing cost alone, without reference to children or the condo; the direction of its signal (higher price points are tighter) agrees with the combined cash-flow check's direction, even though the two are not calculating the same thing. With the updated child-cost figures, the combined cash-flow check now flags a wider range of price points ($700,000-$800,000, depending on the dollar basis used) than the 25%-of-net rule does ($750,000-$800,000 only), whereas in the prior version the combined check flagged only $800,000, a narrower set than the 25%-of-net rule.
  - The 28/36 rule and the price-to-income multiplier (at its 4.0x ceiling) do not flag any price point in this range, including the combinations where the combined cash-flow check shows a narrow or negative monthly result.
- In the single-income scenarios, the divergence is present at every price point and every child count, including 0 children: the rules of thumb in Section 2 are calculated only against the both-working base case (03's Section 1 does not restate them for the single-income scenarios), so there is no direct single-income rule-of-thumb figure to compare against. The combined cash-flow check shows single-income deficits at every combination shown, which is a divergence from the implicit assumption, built into affordability rules of thumb generally, that the qualifying income is stable and continues unchanged.

---

## 5. Emergency Fund Runway Under Income-Loss Scenarios

### Method

- Starting balance: the $70,000 emergency fund after closing costs are paid from it (03, Section 2), which varies by price point because closing costs scale with price.
- Monthly net cash flow in each income-loss scenario = net monthly income (03, Section 1, single-income Partial level) minus all-in monthly housing cost (03, Section 2, base rate) minus the condo carrying cost ($2,735/month, 05, Section 1) minus full monthly living cost (this document's $3,000/month adult baseline placeholder plus Part 2, Child Budget, Section 10, today's dollars).
- Runway in months = starting emergency fund balance / absolute value of the monthly deficit, shown only where the monthly figure is negative (in every scenario modeled here, it is negative).
- Two child-count scenarios are shown: 0 children (income loss occurring before children arrive) and 2 children at peak overlap (income loss occurring during the highest-cost child-rearing phase). The 1-child case falls between these two and is not tabulated separately here. The 0-children figures below are unchanged from the prior version of this document, since they do not depend on child costs; the 2-children figures are recalculated using Part 2 (Child Budget) Section 10's Phase 2 figure.

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
| $600,000 | $54,701 | -$4,865 | 11.2 |
| $650,000 | $53,352 | -$5,281 | 10.1 |
| $700,000 | $52,002 | -$5,698 | 9.1 |
| $750,000 | $50,653 | -$6,114 | 8.3 |
| $800,000 | $49,304 | -$6,531 | 7.5 |

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
| $600,000 | $54,701 | -$5,893 | 9.3 |
| $650,000 | $53,352 | -$6,309 | 8.5 |
| $700,000 | $52,002 | -$6,726 | 7.7 |
| $750,000 | $50,653 | -$7,142 | 7.1 |
| $800,000 | $49,304 | -$7,559 | 6.5 |

- In every income-loss scenario modeled, monthly cash flow is negative even with 0 children, because the combination of housing cost and the condo carrying cost exceeds a single income at every price point tested.
- Runway is highest for the 0-children, Kate's-income-only scenario at the lowest price point (161.4 months) and lowest for the 2-children, Lucas's-income-only scenario at the highest price point (6.5 months, down from 7.1 months in the prior version, because the higher Phase 2 child-cost figure widens the monthly deficit).
- The 2-children runway figures are shorter across the board than in the prior version of this document (for example, Kate's-income-only at $600,000 falls from 12.9 to 11.2 months), reflecting the higher Phase 2 monthly cost in Part 2 (Child Budget). The 0-children figures are unaffected, since they do not include any child-cost line.
- These figures assume unchanged spending during the income-loss period (no reduction in discretionary costs); per `shared/known-modeling-issues.md` (issue 16), a scenario that allows for spending cuts during a shortfall would show a longer runway than the figures above.

---

## 6. Mortgage Rate Sensitivity on the Combined Picture

### Method

- Uses the both-working base-case net income ($16,182/month), the condo carrying cost ($2,735/month), and the 2-children peak-overlap living cost in today's dollars ($3,000 + $4,526 = $7,526/month, using Part 2 (Child Budget) Section 10's start-of-phase figure, consistent with Sections 3 and 5 above).
- All-in monthly housing cost at each price point and rate comes from `03-home-affordability/README.md` Section 3: base rate 6.55%, +100 basis points (7.55%), +200 basis points (8.55%).

| Price | Combined surplus/deficit @ 6.55% | Combined surplus/deficit @ 7.55% | Combined surplus/deficit @ 8.55% |
|---|---|---|---|
| $600,000 | $1,851 | $1,581 | $1,302 |
| $650,000 | $1,435 | $1,132 | $818 |
| $700,000 | $1,018 | $682 | $333 |
| $750,000 | $602 | $231 | -$153 |
| $800,000 | $185 | -$219 | -$638 |

- With the updated (higher) child-cost figures, the combined picture is tighter at every rate than it was in the prior version. At $800,000, the combined figure is already close to zero at the base rate ($185/month) and turns negative at just +100 basis points (7.55%, -$219/month); at +200 basis points it deepens to -$638/month. In the prior version, $800,000 did not turn negative until +200 basis points, and only to -$12/month.
- At $750,000, a 200 basis point rate increase now pushes the combined figure negative as well (-$153/month), which did not happen in the prior version (previously $750,000 remained positive, at $473/month, across the full rate-stress range).
- At $700,000 and below, the combined figure remains positive across the full rate-stress range shown, though the margin at $700,000 narrows to $333/month at +200 basis points, tighter than the prior version's $959/month at the same stress level.

---

## Sources

- `shared/assumptions.md` (combined gross income, down payment, emergency fund, other-debt statement).
- `shared/known-modeling-issues.md`, issue 1 (baseline living expenses must be netted from any surplus figure) and issue 16 (emergency fund runway should note whether it assumes unchanged spending).
- `02-future-budget/README.md`, Part 2 (Child Budget), Sections 2-3 (childcare and children's health insurance premium, carried forward and re-verified), Sections 4-7 (food, clothing, entertainment/activities, camps, youth sports, and vacation increment, new in this version), Section 8 (inflation assumptions), Section 9 (phase-by-phase start/end detail, today's dollars and nominal dollars), Section 10 (primary reference table, monthly child-attributable cost by phase), and Section 11 (scope exclusions, including the adult baseline now handled in Part 1, Adult Budget).
- `02-future-budget/README.md`, Part 1 (Adult Budget) (intentionally blank fillable template for adult-only household costs; cited here as the reason this document now states its $3,000/month adult baseline as its own explicit placeholder rather than attributing it to a populated source document).
- `03-home-affordability/README.md`, Sections 1, 2, and 3 (net monthly income by scenario, all-in monthly housing cost by price point, closing costs and post-closing emergency fund balance, mortgage rate sensitivity).
- `05-seattle-condo-decision/README.md`, Sections 1 and 2 (condo carrying cost baseline, rental scenario rents).
- Bankrate, "What is the 28/36 rule for home affordability?", published June 2, 2026: https://www.bankrate.com/mortgages/what-is-the-28-36-rule/
- Ramsey Solutions, "How Much House Can I Afford?": https://www.ramseysolutions.com/real-estate/how-much-house-can-i-afford
- HomeLight, "10 Rules of Thumb to Determine How Much House You Can Afford," published June 24, 2026: https://www.homelight.com/blog/buyer-how-much-house-can-i-afford-rule-of-thumb/
- Fannie Mae Selling Guide, B3-3.1-08, "Rental Income": https://selling-guide.fanniemae.com/sel/b3-3.8-01/rental-income

## Method Notes Addressed From Known Modeling Issues

This document addresses issue 1 from `shared/known-modeling-issues.md` directly: the combined cash-flow figures in Sections 3, 5, and 6 net out the $3,000/month adult baseline living cost in addition to child-attributable costs and housing, rather than presenting a surplus that omits it, and Section 1 now states plainly that this $3,000/month figure is this document's own carried-forward placeholder rather than a figure sourced from a populated document, since Part 1 (Adult Budget) is an intentionally blank template. It also addresses issue 16 by stating explicitly that the emergency fund runway figures in Section 5 assume unchanged spending during an income-loss period, not a reduced-spending scenario. Every dollar figure describing housing cost, child-rearing cost, and condo carrying cost is cited to a specific section of `02-future-budget/README.md` (Part 1 or Part 2), `03-home-affordability/README.md`, or `05-seattle-condo-decision/README.md` per this document's stated purpose of making the dependency chain auditable. Prose throughout states what the numbers show without advice-toned framing, consistent with the tone requirement in `shared/assumptions.md`.
