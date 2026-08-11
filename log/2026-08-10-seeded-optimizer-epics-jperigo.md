---
date: 2026-08-10
author: Courtney <jperigo@gmail.com>
type: planning
scope: [board]
summary: Structured the scenario-seeded optimizer work as two phased epics — GUI (AW-327 under AW-249) and API (AW-328 under AW-248) — with ten stories; the GUI epic carries one story dependent on the API epic.
issues: [AW-327, AW-328, AW-329, AW-330, AW-331, AW-332, AW-333, AW-334, AW-335, AW-336, AW-337, AW-338]
---

# Seeded-Optimizer Work Structured as Two Phased Epics

## Context

Stakeholder feedback on the newly shipped budget optimizer: starting from zero with dollar ranges is too heavy a lift; planners want to start from a base plan with percentage constraints. The owner approved a design (a completed scenario run seeds the optimizer; constraints are relative stances) and a two-phase delivery, then asked for the board items to be created.

## What Happened / Decided

Created two epics with their stories, all in Backlog, default priority:

- **AW-327 — Budget Optimizer: Scenario-Seeded Constraints** under **AW-249** (InsightCore GUI v2). Stories AW-329 (seed from a run), AW-330 (stance controls compiling to the existing constraints contract), AW-331 (feasibility strip + policy-excluded rows), AW-332 (base-linked comparison and re-optimize), AW-333 ([QA] production verification), AW-334 (adopt the API-native contract; depends on AW-328).
- **AW-328 — Budget Optimizer: API-Native Base Plans** under **AW-248** (InsightCore API v2). Stories AW-335 (base_plan block with provenance), AW-336 (national channel constraints), AW-337 (binding-constraint advisories), AW-338 ([QA] deploy + runner verification).

Labels follow the InsightCore convention: `DataScience`, `InsightCore`, `api`/`gui`, `client-shared`, `group-data-science`, `group-platform` (no `Modeling`), plus `QA` on the QA stories.

## Rationale

Two epics rather than one, per the layer rule: an epic has one parent and the outcomes are separable — the GUI phase ships value alone against the existing API contract, and the API phase is independently shippable. The cross-layer dependency is carried as a single story (AW-334) inside the GUI epic rather than a third epic, because the adoption work is one unit, not a shippable outcome. Phasing exists because the GUI-only compile needs no API change and de-risks the contract design with real usage before the API commits to it. The dependency direction is stated on AW-334 and in AW-328's risks so neither epic's Done is ambiguous: AW-327 cannot close before AW-328 delivers.

## Follow-ups

- Groom AW-329 → AW-333 into Selected for Development when the GUI phase is picked up.
- AW-334 stays unstartable until AW-328's build stories are Done — check the dependency at grooming.
