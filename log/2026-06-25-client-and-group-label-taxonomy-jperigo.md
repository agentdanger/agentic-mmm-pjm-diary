---
date: 2026-06-25
author: Courtney Perigo <jperigo@gmail.com>
type: convention-change
scope: [board, conventions]
summary: Added two prefixed label families to the AW board — client-* (exactly one per item; find all of a client's work) and group-* (the discipline that does the work). group-data-science goes on every item as the Modeling-board membership label; group-mlops / group-data-eng / group-analytics / group-platform layer on to slice the data-eng / MLOps / DS group meeting. Applied across all 66 DataScience items.
issues: []
---

# Client + Group Label Taxonomy

## Context

The board needed to answer two recurring questions the existing labels couldn't: "show me everything for one client" (for per-client team meetings) and "show me one discipline's work" (for the standing data-engineering / MLOps / data-science group meeting). `DataScience` is on everything and `Modeling` on most, so neither discriminates client or doer.

## What Happened / Decided

Adopted two prefixed label families, documented in [board.md](../board.md) and applied across all 66 `DataScience` items:

- **`client-*` — exactly one per item:** `client-whataburger`, `client-jdsports`, `client-sprouts`, `client-shared` (cross-client / methodology / infrastructure / platform). Distribution at rollout: 31 JDS, 16 WAB, 17 shared, 2 Sprouts.
- **`group-*` — the discipline that does the work:**
  - **`group-data-science` on EVERY item** — the Modeling-board membership label (the explicit requirement: all DataScience work must surface on the Modeling board). It doubles as the default "data-science is the doer."
  - One further `group-*` only when the doer isn't data science: **`group-mlops`** (10 — deploys, dependency/env upgrades, reproducible env, automated runs, artifact handoff), **`group-data-eng`** (6 — feeds, ingestion, data SLA), **`group-analytics`** (5 — requirements, readouts, input documentation), **`group-platform`** (2 — InsightCore API v2 / GUI v2).

Existing labels were preserved (append-only); nothing was clobbered.

## Rationale

- **Prefixes (`client-` / `group-`)** keep the families grouped and unambiguous in Jira's flat label space and make `labels in (...)` queries clean.
- **`group-data-science` on everything, not as a discriminator.** The hard requirement was Modeling-board membership for all items, so it can't also mean "only DS work." The *other* `group-*` labels are the real discriminators; a pure-DS item is simply the one with no other `group-*`.
- **`group-platform` over folding InsightCore into `group-mlops`.** The InsightCore API/GUI is app/front-end engineering, and the front-end seat is a known capability gap — giving it its own label makes that work (and the gap) trackable rather than hidden inside MLOps.
- **`DataScience` (team) vs `group-data-science` (discipline)** is a deliberate near-collision, called out in board.md so future agents don't conflate them.

## Follow-ups

- Standing JQL for the meetings: per-client `labels = client-<slug>`; per-discipline `labels = group-<discipline>`; whole technical group `labels in (group-data-science, group-mlops, group-data-eng, group-platform)`.
- New items must get exactly one `client-*` and `group-data-science` (+ a discipline `group-*` if not DS) — fold into the trackability checklist on the next conventions pass.
