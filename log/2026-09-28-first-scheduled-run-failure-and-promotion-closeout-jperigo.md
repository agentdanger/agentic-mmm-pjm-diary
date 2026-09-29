---
date: 2026-09-28
author: Courtney <jperigo@gmail.com>
type: grooming
scope: [board]
summary: The first scheduled JD Sports fit failed at submission, and the day's recovery went onto the board. AW-434 was created Done under AW-245 for the defect and its fix; AW-400 got a comment and stays open for the 10-05 unattended run; AW-410 and AW-432 closed once the hand-submitted fit was promoted and verified on the host. A failure-alert story was drafted and declined by the owner.
issues: [AW-245, AW-400, AW-410, AW-432, AW-434]
---

# First Scheduled Run Failure and Promotion Close-out

## Context

Monday 2026-09-28 was the first unattended run (AW-400) and the first promotion (AW-410), which AW-432 also waited
on. The run failed before its step started; a hand-submitted run of the same pipeline was promoted instead. The owner
asked for the work items to be brought current.

## What Happened / Decided

| Key | Change | Outcome recorded |
| --- | --- | --- |
| AW-434 | Created under AW-245 as a `[Bug]` Story, straight into Done | Empty `git_commit` pipeline input; documented `--set` rejected by the CLI; fixed in mmm-eom-jdsports `97ce746`; schedule recreated with the commit stored |
| AW-400 | Comment; stays In Progress | Failure recorded with the job id; the hand run named and excluded; first unattended run now 2026-10-05 |
| AW-432 | Comment, then acceptance criteria ticked and Done | Host sync verified (advisories, `digital_brand` in the saturation view, mask); promotion criterion met through AW-410 |
| AW-410 | Criteria ticked, comment, Done | Fit `…899ce655` promoted 15:57 UTC; blob-step defect fixed in `c406069` with `--blob-only`; host mask identical to the shipped sidecar |

Drafted and **not** created, by the owner's decision: a `[Build]` story under AW-245 for alerting on a failed
scheduled run.

## Rationale

**AW-434 as its own Bug, created Done.** It is a defect with a reproduction, a root cause and a commit, and it has an
owner-visible consequence (a lost week). The 2026-09-11 and 2026-09-24 precedent applies: finished work with its
commit goes onto the board as Done rather than sitting in Backlog.

**AW-400 stays open.** Its criteria describe the scheduled trigger and the instance's own window. A hand-submitted
run proves the pipeline, not the schedule, so it does not count.

**AW-432 closed on a hand-submitted fit.** Its last criterion reads "Monday's scheduled fit promoted"; the intent was
that the served fit be one the record holds with the new grouping, which the Monday hand run satisfies. The comment
says so, rather than leaving a finished story open on a technicality.

**The blob-step defect lives on AW-410, not in its own story.** It was found and fixed inside AW-410's own work in
the same hour, and the comment carries the commit. A separate Bug would only restate that comment.

**The owner's convention on evidence grades** (partly measured counts as measured; only calibrated-by-allocation
channels are called out, as uncalibrated) applies to client material, not to board items. It is recorded in the
modelling diary.

## Follow-ups

- AW-400: verify the 2026-10-05 run in `model.jds_fit_runs` and close.
- The brand / co-op / performance work for the client's FY28 question (mmm-eom-jdsports `27cb217`, `3226d53`) has no
  board item; the owner decides whether it gets a story under AW-370 beside AW-430.
- Still owed from 2026-09-24 and 2026-09-26: assignees on the items created since then (AW-432 has none), and an
  InsightCoreMCP epic for AW-427, AW-429 and AW-433.
