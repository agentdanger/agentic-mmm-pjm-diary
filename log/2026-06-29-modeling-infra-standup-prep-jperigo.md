---
date: 2026-06-29
author: Courtney Perigo <jperigo@gmail.com>
type: grooming
scope: [board, initiatives]
summary: Prepped the first modeling-infrastructure standup with the engineering + ops team by grooming the AW-243 Modeling Infrastructure MVP. Folded the missing AW-256 into the initiative's definition of done (seven → eight epics), reordered the DoD to the dependency build-sequence, ran a gap analysis (orchestration/alerting, compute/cost, governance, onboarding) and deliberately HELD MVP scope, and set the kickoff-touchbase framing. Updated board.md to eight epics.
issues: [AW-243, AW-256, AW-246, AW-244, AW-226, AW-245, AW-247, AW-125, AW-238, AW-248, AW-249]
---

# Modeling Infrastructure Standup Prep — AW-243 Grooming

## Context

First standup / touchbase with the engineering and ops team on modeling infrastructure (non-client-specific work). Groomed the AW-243 Modeling Infrastructure MVP for readiness and prepared the agenda before holding the meeting.

## What Happened / Decided

- **Readiness verdict:** AW-243 is well-framed (bounded MVP, clear DoD, per-discipline `group-*` labels) and ready for a **kickoff / alignment** touchbase — not a status board-walk. Only one of the eight capability epics is actually In Progress (AW-246 Reproducible Environment, spike AW-250 @Anagh); 2 of 14 items are owned; five epics are still bare shells (no stories). So the meeting's job is align → assign → sequence, not status reporting.
- **AW-243 DoD restructured.** The initiative description listed only **seven** capabilities — AW-256 (Development & Production Training Datasets), created 2026-06-25 as the eighth epic, had never been folded in. Added it and updated the count to **eight**. Reordered the DoD list to the **dependency build-sequence** (not key order) and added a note saying so: reproducible env (AW-246) → automated ingestion (AW-244) → data SLAs (AW-226) → dev/prod training datasets (AW-256) → automated runs (AW-245) → artifact versioning & handoff (AW-247) → QA (AW-125) → knowledge base (AW-238).
- **Gap analysis — scope HELD.** Identified topics that are neither in the eight epics nor in the description's explicit out-of-scope list (which already defers drift monitoring, a full model registry, notebook CI/CD, secrets management): **orchestration + run-failure alerting/observability** (the strongest gap — sequencing ingest→run→publish, retries, alerting a human on a failed run), **compute & cost management** for automated GPU runs, **access control / data governance** beyond secrets, and a **new-model/client onboarding scaffold**; plus adjacent items (experiment tracking, a shared validation/backtesting harness, a rollback runbook). Decision: **leave MVP scope as-is for now** — do not add a ninth epic or expand the description; revisit if the standup surfaces the need.
- **Standup framing agreed:** (1) lead with the bounded-MVP framing (these eight = the finish line); (2) walk the dependency spine starting at the live AW-246; (3) assign epic owners (seven of eight unowned) via the `group-*` discipline mapping; (4) agree the next kickoff `[Spike]` for the top 2–3 epics; (5) flag-and-park InsightCore v2 (AW-248 / AW-249 — initiatives with no epics, platform/reporting layer) as possibly a separate forum; (6) move AW-243 to In Progress once work is officially underway.
- **board.md updated** to describe AW-243 as an **eight-epic** MVP (closes the follow-up left open on 2026-06-25).

## Rationale

- **Eight, not seven.** AW-256 was always meant to be the eighth capability; the description and board.md were simply stale. Folding it in keeps the bounded-MVP DoD honest — the initiative is Done when these eight epics are Done.
- **Order the DoD by build sequence.** The capabilities form a value chain — get a model to run reproducibly on reliable data, automate the run, version its outputs, QA the whole thing, document it. Ordering the DoD that way makes backlog priority and the eng↔ops hand-offs legible, and the "not by key" note stops a future reader from re-sorting it.
- **Hold the gaps deliberately.** Keeping the MVP bounded is the entire point of AW-243. The gaps (especially orchestration + failure alerting) are real, but the owner chose to settle scope in/after the standup rather than pre-expand it. Recorded here so they read as *considered-and-held*, not missed.
- **Kickoff, not status.** With only AW-246 in flight, treating this as a status standup would misframe it; alignment + ownership + sequencing is the right shape for a first cross-functional touchbase.

## Follow-ups

- Hold the standup; assign an owner to each unowned epic; agree the kickoff `[Spike]` for the top 2–3 priority epics.
- Decompose the five epic shells (AW-244, AW-226, AW-245, AW-247, AW-125) — each likely opens with a scoping `[Spike]`.
- Move AW-243 → In Progress once work is officially underway (AW-246 already is).
- Decide whether InsightCore v2 (AW-248 / AW-249) belongs in this eng/ops forum or a separate platform discussion.
- Revisit the held gaps — orchestration + run-failure alerting first — if the standup surfaces the need.
