# Context for Claude

This repo holds financial planning exercises for **Kate & Lucas** (a couple), worked through with Claude.

## Household context

- Location goal: Portland, OR (home purchase).
- Near-term goals: saving for a house down payment and a wedding.
- Longer-term goals: having 1-2 kids, owning a home.
- One exercise compares the 2001 home-buying experience (Kate/Lucas's parents) to buying in 2026.

## Repo layout

- `shared/` — common inputs/assumptions (income, savings, debts, rates) referenced by multiple exercises. Keep these consistent across folders rather than restating numbers in each one.
- `01-current-budget/` — current household budget.
- `02-future-budget/` — budget projected forward assuming kids + a home purchase.
- `03-home-affordability/` — comfortable home price given 1-2 kids.
- `04-2001-vs-2026-comparison/` — parents' 2001 purchase vs. today.

## Working notes

- This is currently a scaffold — folders are empty aside from placeholder READMEs.
- Another existing repo will be referenced for prior analysis; not yet linked here.
- When filling in an exercise, update `shared/` first if it introduces a new assumption other exercises should reuse.
