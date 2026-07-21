# Context for Claude

This repo holds financial planning exercises for **Kate & Lucas** (a couple), worked through with Claude.

## Household context

- Location goal: Portland, OR (home purchase).
- Near-term goals: saving for a house down payment and a wedding.
- Longer-term goals: having 1-2 kids (planned 2 years apart), owning a home.
- One exercise compares the 2001 home-buying experience (Kate/Lucas's parents, Ann Arbor, Michigan) to buying in 2026 (Portland).
- An existing Seattle condo is a separate asset/decision, analyzed on its own.

## Repo layout

- `shared/` - common inputs/assumptions (income, savings, debts, rates) referenced by multiple exercises, plus `known-modeling-issues.md`, a running list of calculation mistakes identified in earlier drafts. Keep assumptions consistent across folders rather than restating numbers in each one; keep the issues list current if new mistakes are found.
- `01-current-budget/` - current household budget.
- `02-future-budget/` - cost of raising two children (spaced 2 years apart): childcare, children's health insurance, and general child-related living cost increases, with inflation projected forward over the child-rearing window. This is an input document; it does not draw affordability conclusions itself.
- `03-home-affordability/` - home-purchase cost mechanics only: after-tax income by scenario, all-in monthly housing cost by price point, closing costs, mortgage rate sensitivity. Does not include child costs or a combined affordability verdict. This is an input document.
- `04-2001-vs-2026-comparison/` - parents' 2001 purchase vs. today.
- `05-seattle-condo-decision/` - keep or sell the existing Seattle condo.
- `06-affordability-assessment/` - the combined analysis: takes `02` and `03` (and `05`'s condo carrying cost) as inputs and tests standard home affordability rules of thumb (28/36 rule, 25%-of-net-income rule, price-to-income multiplier) against the full cash-flow picture. This is where "can we actually afford this" gets answered; `02` and `03` deliberately do not answer that question on their own.

## Working notes

- `01` through `06` have real content as of July 2026. Each analysis document cites its sources and, where it depends on another document's numbers, states exactly which section those numbers came from.
- Each folder's `README.md` holds the full report directly, so GitHub's folder-level README rendering shows the actual content immediately, rather than a pointer to a separate file. `02-future-budget/README.md` is a single merged document with two parts (Part 1: Adult Budget, Part 2: Child Budget); cross-references between the two parts use "Part 1"/"Part 2" rather than the old separate filenames.
- Tone across all analysis documents: neutral and objective. No persuasive framing, no advice-toned verdicts, no rhetorical questions. State what the numbers show and cite every external data point with a source and date.
- Format: every calculation is explained in bullet points before the table of resulting numbers, not the other way around. No em dashes.
- When filling in or revising an exercise, update `shared/assumptions.md` first if it introduces a new assumption other exercises should reuse, and check `shared/known-modeling-issues.md` so past mistakes aren't repeated.
- If `02` or `03` are revised, `06` should be checked and updated too, since it pulls specific numbers from both by section reference.
