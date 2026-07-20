# Shared Assumptions

Confirmed by Kate & Lucas, July 2026. All downstream analyses (home affordability, condo decision, 2001 vs. 2026 comparison) should use these as the starting facts rather than re-deriving them, and should flag explicitly if a given analysis needs to deviate from one of them.

## People & Income

- Kate: $165,000/yr gross
- Lucas: $143,520/yr gross
- Combined: $308,520/yr gross
- Filing status: Married Filing Jointly
- Other debts: none significant (no student loans, no car payments affecting DTI)

## Savings & Cash

- Down payment pool: $200,000 ($100K Kate savings + $50K Kate family gift + $50K Lucas savings)
- Emergency fund: $70,000 ($35K each), kept separate from the down payment. Do not count it toward the down payment. Closing costs, if paid from it, should be shown as reducing it.

## Target Home Purchase (Portland, OR)

- Price range: $600,000 to $800,000, in $50,000 increments
- Neighborhoods: Mt. Tabor, Laurelhurst, Sellwood-Moreland
- Mortgage: 30-year fixed
- Down payment: $200,000 actual dollars (not a 20% assumption) - use actual figures for loan amount, LTV, and PMI applicability
- Mortgage rate, property tax rate, insurance cost, and maintenance cost should be verified against current data as of this analysis, not assumed from older source material

## Existing Asset: Seattle Condo

- 1740 NE 86th St #319, Maple Leaf, Seattle, WA 98115
- 641 sq ft, 1BR/1BA, elevator building, in-unit washer/dryer, covered parking
- Purchased August 2022 for $339,000
- Remaining loan balance: $305,000
- Monthly carrying cost baseline: PITI $2,017 + HOA $435 + maintenance reserve ~$283 = ~$2,735/mo (verify or update if better data is available)
- Currently held as a rental; the keep-or-sell decision is its own analysis (see `05-seattle-condo-decision/`). Other analyses should treat its carrying cost as a fixed input line, not re-litigate the keep/sell decision.

## Children (planned, not yet born)

- Two children planned
- Cost inputs (daycare, health insurance, general child costs) should be researched against current Multnomah County / Portland-area data rather than assumed

## Parents' Historical Home Purchase (for the 2001 vs. 2026 comparison)

- Address: 4663 Erin Court, Ann Arbor, Michigan
- Purchase year: 2001
- Purchase price: $540,000
- Combined household income at the time: $177,500/yr
- State: Michigan (a flat-rate state income tax state - confirm the actual 2001 rate, which differs from the current rate)

## Ground Rules for This Round of Analysis

- Treat the figures above as given.
- Do not carry forward unverified assumptions from prior drafts (mortgage rates, tax brackets, insurance costs, daycare costs, inflation figures) without checking them against current, citable data.
- See `known-modeling-issues.md` for specific errors identified in the prior version of this work. Do not repeat them.
- Tone: neutral and objective. No persuasive framing, no rhetorical questions, no verdicts phrased as advice ("you should," "do not proceed"). State what the numbers show and let the reader draw conclusions.
- Format: markdown. Explain each calculation in bullet points, then present the actual numbers in a table.
- No em dashes.
- Cite sources (with dates) for any external data point: tax brackets, mortgage rates, inflation/CPI, insurance costs, daycare costs, real estate comps.
