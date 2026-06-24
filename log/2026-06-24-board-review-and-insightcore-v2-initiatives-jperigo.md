---
date: 2026-06-24
author: Courtney Perigo <jperigo@gmail.com>
type: planning
scope: [board]
summary: Walked the live AW board (63 DataScience items), flagged five trackability gaps (orphan epic AW-123, unassigned active epics, migration-epic/child status mismatch, empty Selected-for-Development, high WIP), and created two orphaned Initiatives — InsightCore API v2 (AW-248) and InsightCore GUI v2 (AW-249) — left in Backlog to be planned out later.
issues: [AW-248, AW-249, AW-123, AW-230, AW-231, AW-234, AW-227, AW-243]
---

# Board Review + InsightCore v2 Initiatives

## Context

Pulled the live AW board to confirm current structure and surface anything that had drifted from the conventions, then stood up two new top-level Initiatives to home the upcoming reporting-layer (InsightCore API + GUI) version-2 work. The initiatives are deliberately empty for now — the contents get planned in a later pass.

## What Happened / Decided

- **Live board read** via `searchJiraIssuesUsingJql` (`labels = DataScience`): 63 items — 3 Initiatives, 13 Epics, 47 Stories — across the three known lines (v0.17 historical AW-152, v0.19 model work AW-153, Modeling Infrastructure MVP AW-243).
- **Two new Initiatives created** (Backlog, no parent, as requested — planning to follow):
  - **AW-248 — InsightCore API v2** · labels `DataScience`, `InsightCore`, `api`.
  - **AW-249 — InsightCore GUI v2** · labels `DataScience`, `InsightCore`, `gui`.
  - Each carries a capability statement plus candidate pillars (a starting frame, not a committed scope); the epic set and bounded definition of done are explicitly deferred to planning.
- **New label coined: `InsightCore`** — did not previously exist in the `DataScience` item set. Used to group the reporting-layer initiatives.
- **`Modeling` label intentionally omitted** on both new initiatives — these are the reporting/serving layer; model training is out of scope for those repos, so `Modeling` would be misleading.

## Rationale

- **Why Initiatives, not Epics.** API v2 and GUI v2 are each a durable, multi-quarter capability that several epics will hang off — the Initiative test ("a capability we're building, not a piece of work"). They are not yet bounded with a definition of done; that is acceptable for a Backlog initiative created expressly to be planned, and the bounding (enumerate epics → declare DoD) is the first planning task, per the *initiatives are bounded* convention.
- **Why a separate `InsightCore` label instead of `Modeling`.** The board's `Modeling` label tracks MMM model work on the version lines. The InsightCore repos consume trained artifacts; mixing them into `Modeling` would blur the search boundary the label exists to keep. `InsightCore` + `api`/`gui` keeps the reporting work independently findable.
- **Orphaned on purpose.** Initiatives sit at the top of the hierarchy (no parent by design), so "orphaned" here just means no epics linked yet — intentional until planning assigns them.

## Follow-ups

- **Plan AW-248 / AW-249:** convert candidate pillars into epics and declare each initiative's bounded definition of done.
- **Trackability gaps flagged during the read** (not yet actioned, owner's call):
  - **AW-123** (*InsightCore – PyMC Bayesian model*, Epic, Done) is parentless — re-parent under a line (AW-152 historical) or consciously leave as legacy.
  - **Unassigned active epics** — AW-227, AW-230, AW-234, and the whole AW-243 tree have no assignee.
  - **Status mismatch** — migration epics AW-230 / AW-234 sit in Backlog while AW-230's `[Build]` child AW-231 is already In Progress.
  - **`Selected for Development` is empty** — nothing staged between Backlog and In Progress.
  - **High WIP** — ~9 items In Progress across many epics.
