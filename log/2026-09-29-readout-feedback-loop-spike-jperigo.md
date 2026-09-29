---
date: 2026-09-29
author: Courtney Perigo <jperigo@gmail.com>
type: decision
scope: [board]
summary: At the close of the Q2 FY2027 readout work the owner put a readout feedback loop on the roadmap: keep the delivered deck with its build inputs so any quarter can be rebuilt, and possibly automate the quarterly build. Created as AW-435, a [Spike] under AW-370, in Backlog. The day's finished work (reworded evidence advisories and the promoted refit; the readout's leaderboard, static slides and narrative) was drafted as two Done stories and deliberately not created.
issues: [AW-435, AW-370, AW-384, AW-400]
---

# Readout Feedback Loop Spike

## Context

The Q2 FY2027 readout is now a template, a snapshot, a narrative file and a build, finished by hand in PowerPoint.
Closing out the day, the owner asked for the delivered presentation to be stored somewhere it can be rebuilt from,
with an automated report as a possible next step.

## What Happened / Decided

| Key | Change |
| --- | --- |
| AW-435 | Created under **AW-370**, Backlog: *[Spike] Readout feedback loop: keep the delivered deck and automate the quarterly build*. Questions: where the delivered deck and its inputs live, how final edits flow back into the template and narrative, whether the build can run after each promoted fit and which steps stay with an analyst. Ends in go/no-go, with [Build] stories if go. |

Drafted and **not** created, by the owner's choice: a [Build] story for the evidence-advisory rewording and the
promoted refit (mmm-jdsports `429c7fb`, mmm-eom-jdsports `a82c685`, schedule `90be54a`, fit `…94851a84`), and a
[Build] story for the readout's leaderboard, static slides and first narrative (mmm-eom-jdsports `90be54a`,
`656a6be`, `156577b`, `9f3b034`, `e97ca02`). Both would have gone in as Done.

## Rationale

**A spike, not a build.** Storage, the feedback path and the degree of automation are open choices (OneLake beside the
fit or SharePoint; what an unattended build may draft; where the review gate sits), and automation was offered as
"potentially". A go/no-go keeps the build stories from asserting answers nobody has given.

**Under AW-370, labelled `client-jdsports`.** The readout tooling lives in the JD Sports production repo and AW-430,
the template, sits there. If the loop generalises to Whataburger, the build stories can move to a shared epic then.

## Follow-ups

- AW-384 (disclose the ranking change) is now pressing: the Q2 deck does not yet explain why CTV, Linear TV and OOH
  read well below the Q1 message the client heard.
- AW-400: verify the 2026-10-05 scheduled run and close.
- Assignees remain unset on every item created since 2026-09-24, AW-435 included.
