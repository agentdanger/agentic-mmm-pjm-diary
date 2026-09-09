---
date: 2026-09-09
author: Courtney Perigo <jperigo@gmail.com>
type: decision
scope: [board]
summary: AW-342 closed with its output finally recorded, AW-343 reassigned from Anagh to Courtney and its open question settled, and AW-281 unblocked. Also records why the specification looked stalled when the analysis was complete — the third story in this epic to be finished without the handoff being written down.
issues: [AW-342, AW-343, AW-281, AW-280, AW-279, AW-291, AW-253]
---

# AW-342 Closed, AW-343 Reassigned, and a Third Missing Handoff

## Context

AW-342, the channel-tactic breakout specification, showed In Progress with no
comments and no update since the day it was created, while Victoria reported the
analysis complete. Its receiving story, AW-343, was assigned to Anagh but the work
was about to be done elsewhere.

## What Happened / Decided

**AW-342 is Done.** The analysis was complete; the story was open because the
handoff was never written down. Its output is a Fabric notebook in `Data_Tech_Dev`
carrying, per candidate, the parent channel, the resulting channels, the mapping
rules, spend-history depth, geo coverage and flighting correlation. That is now
recorded on the issue, along with the approved list and the grain, and AW-342 is
linked to AW-343 as a blocker.

**Two approved candidates, both Go.** `Google_DMA` and `Meta_DMA`, each splitting
into Brand, COOP and BAU-Performance on `Campaign_Name` rules. The rules supersede
the manual `Brand_Coop` field. Notably the feed already carries
`Google_Brand_Coop` and `Meta_Brand_Coop` columns; the rules-based classification
was preferred over them on the evidence in AW-279.

**AW-343 reassigned from Anagh to Courtney**, since the build is happening in the
JDS gold work rather than against the production training dataset.

**Owner decision on the open question: `appdownload` classifies as Loyalty, not
Brand.** The AW-279 notebook was inconsistent — its pandas pass says Loyalty, its
PySpark pass maps to Brand with a note that loyalty is not needed. Consequence:
**Google carries four tactics, Meta carries three.** Recorded on AW-343.

**AW-281 is unblocked.** Its first acceptance criterion was the reconciled candidate
list, which now exists.

## Rationale

**The specification was not late; the record was.** AW-342's own description notes
that AW-280 closed without its output recorded, and that the business requirements
would have to be recovered as a result. AW-342 was heading for the same ending one
story later. That is three stories in this epic — AW-280, AW-291 and AW-342 — where
the analysis finished and the Definition of Done clause requiring the landing place
to be recorded was not met.

The pattern is worth naming because the cost is not bookkeeping. It is that the next
story cannot start, and the one after that re-derives work already done. AW-281 sat
in Backlog for a week for exactly this reason.

**Reassignment rather than a parallel story.** AW-343 describes precisely the work
being done in the gold build. Creating a second story would have produced two people
deriving the same columns, which is the failure the epic's discovery/implementation
split exists to avoid.

**The dev-only constraint is respected and matters.** AW-343 requires production
untouched and says columns graduate only on a go verdict. The breakouts are being
built into the development gold layer, alongside the unchanged parent columns, so a
no-go is a column drop rather than a rebuild.

## Follow-ups

- Amend the Definition of Done, or the grooming checklist, so a story cannot move to
  Done without a recorded output. Three misses in one epic is a process gap, not
  three oversights.
- Confirm with Anagh that AW-343 moving off him is expected.
- AW-281 needs the dev dataset identifier once the gold build runs; the story asks
  for it explicitly.
- The `Google_Brand_Coop` and `Meta_Brand_Coop` columns already in the feed deserve a
  note on AW-291, since that story asked whether the parsing had landed and the
  answer is that it has, in a form the analysis chose not to use.
