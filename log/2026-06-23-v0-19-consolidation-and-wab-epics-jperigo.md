---
date: 2026-06-23
author: Courtney Perigo <jperigo@gmail.com>
type: planning
scope: [board, conventions]
summary: Stood up this diary, then used it to structure WAB's new-market and input/enrichment work, add the Data Engineering SLA, reopen AW-220, and consolidate every active MMM epic under the v0.19 initiative (AW-153). Retired the legacy AW-47.
issues: [AW-153, AW-220, AW-222, AW-223, AW-224, AW-225, AW-226, AW-227, AW-228, AW-229, AW-217, AW-154, AW-215, AW-47]
---

# v0.19 Consolidation + WAB New-Market / Enrichment Epics

## Context

First working session on the AW board through this diary, alongside the WAB pymc-marketing 0.19.4 migration ([modeling diary, 2026-06-23](../../agentic-mmm-diary/clients/whataburger/sessions/2026-06-23-pymc-marketing-0-19-4-migration-jperigo.md)). Goal: capture the active modeling work as trackable board items and get the hierarchy coherent.

## What Happened / Decided

- **Reopened AW-220** (demo-account v0.17→v0.19 upgrade): was marked Done but regression validation is ongoing → moved back to In Progress with a comment.
- **Created Epic AW-222** (WAB MMM: New-Market Fit — expansion & thin-data markets) under AW-153, with starter stories **AW-223** `[Spike]` (characterize thin-data markets + store↔media confound), **AW-224** `[Build]` (dynamic self-retiring data-limited treatment), **AW-225** `[QA]` (track expansion-market fit metrics). Scoped to *track the new-market fit*, deliberately not cataloguing the candidate architectures.
- **Created Epic AW-227** (WAB MMM: Model Inputs & Enrichment) under AW-153 — the WAB analog of JDS's AW-154 — with **AW-228** `[Data]` (channel-to-grouping business requirements → **assigned Spencer Hall**) and **AW-229** `[Data]` (YouGov brand-equity feature, unassigned).
- **Data Engineering Delivery SLA**: created as Initiative AW-226, then (per the call to keep it with the WAB epics) **converted to an Epic under AW-153**.
- **Consolidated everything under v0.19 (AW-153)**: re-parented AW-217 (WAB Quality Refinement), AW-154 (JDS v2 Enriched), and AW-215 (JDS Quality Refinement) from the v0.17 initiative (AW-152) to AW-153. All seven active MMM epics now ladder up to v0.19; AW-152 holds only Done epics.
- **Retired AW-47** (WAB Model Development) — legacy, untagged, empty, unparented, stale since 2025-11 — closed to Done with a superseded comment pointing to AW-217/222/227.

## Rationale

- **Spike and Bug as Story variants.** AW exposes only Initiative → Epic → Story (no Bug/Spike type), and the team already writes bugs as Stories (e.g. AW-221). The diary codifies this rather than fighting the board config.
- **A separate enrichment epic (AW-227) was necessary**, not a convenience: AW-217 (Quality Refinement) *explicitly excludes* input/channel/feature changes, so channel-mapping requirements and a new YouGov feature can't live there. AW-47 was the only alternative home and it's defunct.
- **One v0.19 line.** With WAB migrating to 0.19.4, consolidating all active modeling epics under AW-153 keeps the roadmap legible; the v0.17 initiative becomes purely historical.
- **Mechanics learned:** an Initiative→Epic type change can't be done in one edit (hierarchy-level change) — change the issue type first, then set the parent. And there is no Cancelled state, so superseded items are retired to Done with an explanatory comment (now noted in [board.md](../board.md)).

## Follow-ups

- Run the migrated v2026_3 `_pmm0194` notebook and update AW-219 / the new-market epic with results.
- Apply the 0.19.4 migration recipe to the JDS notebooks (AW-154 / AW-215 are now on the v0.19 line).
- AW-228: schedule the channel-mapping requirements session with the business (Spencer).
- AW-220: close once regression validation passes.
