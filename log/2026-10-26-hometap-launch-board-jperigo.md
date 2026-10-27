---
date: 2026-10-26
author: Courtney <jperigo@gmail.com>
type: planning
scope: [board, conventions]
summary: Hometap's model launch went onto the board for the first time, on the current client structure. Five epics under AW-153 carry the label client-hometap, coined for this. AW-436 holds discovery, created Done with its commits (9 stories). AW-446 to AW-449 are the four steps to the 2026-11-20 MVP, in Backlog (22 stories, one later folded in). The owner's weekly-update steps "build the transformations" and "create the training data" became one gold training table epic, as AW-371 is for JD Sports. All 36 items are assigned to the owner. AW-450 was folded into AW-460 and retired. Markdown checklists render only without inline formatting.
issues: [AW-436, AW-446, AW-447, AW-448, AW-449, AW-450, AW-451, AW-452, AW-460]
---

# Hometap Model Launch on the Board

## Context

The owner wanted Hometap documented in Jira on the structure used for other clients' launches, with the steps of
her weekly update as epics and the delivered discovery work recorded.

## What Happened / Decided

- **Five epics under AW-153** (the current version line), all `client-hometap` + `group-data-science`:
  - AW-436 *HMT MMM: Discovery and kickoff*, Done, with nine Done stories (AW-437 to AW-445), each citing its
    commits: repos, KPI, geography, media taxonomy, Google's hard-coded start date, earned media, economic
    controls, the kickoff, the spend backfill review.
  - AW-446 *Control data for the MVP* (AW-450 to AW-455), AW-447 *Data storage agreed with Ocean and Hometap
    engineering* (AW-456 to AW-459, adds `group-data-eng`), AW-448 *Gold training table in Fabric* (AW-460 to
    AW-465), AW-449 *MVP model line and the November readout* (AW-466 to AW-471). All Backlog.
- **All 36 items assigned to the owner.**
- **Same day, after Hometap confirmed its calendar:** AW-451 and AW-460 rewritten around the week rule; AW-450
  (footprint events) folded into AW-460 and closed as superseded with a comment; AW-452 took over confirming the
  footprint with Hometap; AW-446's scope moved the footprint out.
- **Label coined:** `client-hometap`.

## Rationale

- **Under AW-153, not a client initiative.** The routing rule puts model work on the current version line under
  AW-153, and every client's epics sit there; an initiative is for a capability spanning clients.
- **Steps 3 and 4 merged.** Transformations without the table they feed are not a shippable outcome; AW-371 holds
  both for JD Sports.
- **Discovery created as Done.** The board is a record (precedent 2026-09-24); the epic shows the launch from its
  start, and each story names where its work landed.
- **AW-450 folded in.** The footprint dates come straight from the KPI, so deriving them belongs with the state
  dimension (AW-460) that uses them; only Hometap's confirmation was separate work, and AW-452 already asks Hometap
  for its business calendar.

## Follow-ups

- Scheduled refits and artifact handoff for Hometap go in as stories under AW-245 and AW-247 after the MVP.
- Earned media and the PR calendar wait for the February read; no items yet.
