---
date: 2026-08-11
author: Courtney Perigo <jperigo@gmail.com>
type: decision
scope: [board, conventions]
summary: Closed AW-327 on what shipped and retired AW-328 undelivered — the GUI phase satisfied planners with no API change, so the API-native phase was closed as not needed. Establishes two practices: amend acceptance criteria to match delivery before closing, and record what a retired item forgoes so a green tick is never read as delivered work.
issues: [AW-327, AW-328, AW-329, AW-330, AW-331, AW-332, AW-333, AW-334, AW-335, AW-336, AW-337, AW-338]
---

# Seeded-Optimizer Close-Out and the Retirement of the API Phase

## Context

The seeded optimizer planned on 2026-08-10 as two phased epics was built and
deployed the following day. Planners used it against a real plan and signed off.
The owner then judged the API phase unnecessary and asked for the whole line to be
closed out.

## What Happened / Decided

**AW-327 (GUI) closed on what shipped.** Delivered: AW-329 (seed from a run),
AW-330 (stance controls), AW-333 (QA). Retired: AW-331 (feasibility strip shipped,
policy-excluded rows dropped), AW-332 (base-linked comparison and re-optimize),
AW-334 (adopt the API-native contract).

**AW-328 (API) retired undelivered**, with all four stories (AW-335–338). No API
work was started; InsightCoreAPI's last commit remains the 2026-08-06 runner fix.

Twelve issues moved in total, all assigned to Courtney. Retirements follow the
board's no-Cancelled-state rule: Done, with a comment whose first line reads
**"Retired, not completed."**

## Rationale

**The phasing worked, and that is why the second phase died.** AW-327 was written
GUI-only precisely so it could ship value against the existing contract and
de-risk the design before the API committed to it. It turned out the optimizer's
constraint vocabulary *already* expressed percentage bands — a market rule in
`range` mode is a target plus a tolerance — so the only thing missing was that the
centre had to be typed by hand. Seeding supplied it, the stakeholder complaint
went away, and the layer underneath was never needed. Worth remembering the next
time a two-phase plan is drafted: the phase boundary is what made this cheap to
stop.

**Acceptance criteria were amended to match delivery before closing, not after.**
The delivered design diverged from the written stories — the entry point moved to
My Runs, a guided modal replaced the seeded stance grid, asymmetric bands were
dropped, and a historical-spend basis was added mid-build. Closing as-written
would have left the board asserting that a Scenario Results entry point and
asymmetric bands exist. The rule adopted: **when delivery diverges, rewrite the
ACs to describe what exists, add a scope note naming what was dropped and why,
then close.** The alternative — closing as-is with an explanatory comment — leaves
a future reader hitting the wrong design first and only learning otherwise from
the comment thread.

**Every retired item records what it forgoes.** A Done tick on a board with no
Cancelled state is ambiguous by construction, and these retirements give up real
capability rather than duplicate work. Each carries the specific consequence:
excluded channels are absent rather than shown as excluded (`other_digital` reads
as headroom elsewhere in the product); nothing bounds a channel summed across
markets, so a national commitment over-constrains when expressed per market;
base-plan provenance stays browser-only; and — the one most likely to be
rediscovered as a defect — **a banded optimization does not report which
constraints were binding at the optimum**, so a planner cannot tell whether the
model pressed against their band or settled inside it. Each names the trigger that
should reopen the question.

**The QA story was narrowed rather than left open.** AW-333's original criteria
covered compare-and-re-optimize, which does not exist. Rescoping it to the seeded
path let it close honestly on planner sign-off and the production deploy, instead
of holding an epic open for verification of something nobody built.

## Follow-ups

- **`deploy_api.sh` still has no `$APP_DIR` guard, and is now tracked by no board
  item.** AW-338 carried the deploy check and has been retired; the guard was
  never opened as its own story. That file has caused two production problems
  (the 07-27 near-repeat of the pre-warm OOM, and the 08-06 stale-runner
  misdispatch). It needs a story under a live epic.
- Asymmetric bands (−x/+y) are recorded as dropped scope on AW-330 rather than
  tracked; open a story only if someone asks for them.
