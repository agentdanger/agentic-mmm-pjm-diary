---
date: 2026-09-11
author: Courtney <jperigo@gmail.com>
type: decision
scope: [board]
summary: Closed out the day — AW-367 raised and Done for the per-period budget defect that invalidated five weeks of multi-week optimizations, AW-368 Done for the eleven-day-late exclusion merge, AW-369 opened for the missing refusal message, and AW-356 reframed as an upgrade spike after finding upstream shipped its carry-in in 1.1.0. AW-348 stays In Progress on three open stories; AW-349 is Done.
issues: [AW-348, AW-349, AW-356, AW-367, AW-368, AW-369, AW-321]
---

# Closing the Day: Per-Period Defect, and AW-356 Becomes an Upgrade Question

## Context

The day's planned work (objective horizon, lagged-effect reporting, queue cap) was already groomed onto the board and deployed when a planner's question about a Dallas CPT surfaced a defect in the optimizer that predated all of it. Closing out means recording both the defect and the two board consequences it produced.

## What Happened / Decided

**AW-367 raised and closed the same evening.** `[Bug] Multi-week optimizations were solved at the period count times their budget` — every optimization on a window longer than one week since 2026-08-06 was solved at `num_periods` × its budget. Fixed in InsightCoreAPI `4be8505` (merged `d8a9006`), deployed 19:19 UTC, and all five quarter optimizations re-run with their original constraints: every market improves at the same spend, +5.5% to +25.5%. Both tables are on the issue.

**AW-368 raised and closed.** The seeded optimizer's percentage-band button had been failing with `constraint_on_excluded_cell` for eleven days; the fix was written on 2026-08-31 and never merged. Merged as GUI `0ae53d6`. **AW-369** opened under AW-348 for the half that is genuinely not done: the refusal carries a stable code but no sentence, which is why a planner worked around it rather than reporting it.

**AW-356 reframed rather than started.** Upstream PR #2898, merged 2026-08-19 and shipped in pymc-marketing 1.1.0, implements the carry-in this story was opened for. The story now reads as a choice — upgrade and inherit it, or build it on the pinned 0.19.4 — and the upgrade is a major version against optimizer internals refactored on 2026-08-17, so it should be scoped as a spike first. Comment recorded on the issue; no re-titling, because the outcome the story asks for is unchanged.

**Board state at close.** AW-348 (API) In Progress on AW-356, AW-357, AW-358 and AW-369. AW-349 (GUI) Done. AW-321 still holds the thinned-draws spike.

## Rationale

AW-367 was created and closed in the same session rather than left as a note, because a defect that silently invalidated five weeks of a shipped capability's output is exactly the kind of thing a future reader needs to find from the board alone — the two tables on the issue are the evidence that the fix worked, and the `spend_basis` field is how anyone can tell a superseded result from a current one.

The AW-356 comment matters more than a status change would. The story was sized as a build against a known divergence; discovering that upstream has already solved it turns the question from "how do we implement carry-in" into "what does an upgrade cost", and those have different owners and different risks. Recording that on the issue stops the next person from building something they could have inherited.

AW-369 exists because the eleven-day gap had two causes and only one of them was the unmerged branch. A planner who sees an error code with no sentence concludes the feature is broken; a planner who sees an explanation reports it. That is a product defect, not a process failure, and it deserves its own item.

## Follow-ups

- Scope the 1.1.0 upgrade as a spike before AW-356 is assigned.
- The standing equivalence check proposed on AW-367 — optimize one multi-week plan per deploy, assert the objective is within a few percent of the scenario's plan-only score — has no board item yet and should get one.
