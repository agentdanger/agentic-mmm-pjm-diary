---
date: 2026-06-24
author: Courtney Perigo <jperigo@gmail.com>
type: planning
scope: [board, conventions]
summary: Built per-client 0.19.4 migration epics (WAB + JDS) with build/QA/deploy stories, added WAB/JDS input-documentation + SSS stories, split a Modeling Infrastructure initiative (AW-243) out of the v0.19 line to home the Knowledge Base and Data SLA, and adopted a hard rule that board items never reference the diaries.
issues: [AW-243, AW-238, AW-242, AW-226, AW-230, AW-231, AW-232, AW-233, AW-234, AW-235, AW-236, AW-237, AW-239, AW-240, AW-241, AW-227, AW-154, AW-153]
---

# Migration Epics + the Modeling Infrastructure Initiative

## Context

Built out version-migration tracking on the AW board and reorganized its top level, alongside the WAB pymc-marketing 0.19.4 modeling work. Goal: every active body of work has a coherent home, and the board's three lines are cleanly separated.

## What Happened / Decided

- **Per-client 0.19.4 migration epics**, each decomposed into `[Build]` re-architecture / `[QA]` / `[Deploy]`:
  - **WAB all-markets** — AW-230 (stories AW-231/232/233); AW-231 moved to In Progress (the re-architected `_pmm0194` production copy already exists). Kept explicitly distinct from AW-222 (WAB new-market fit), which re-architects the expansion markets separately.
  - **JDS v2** — AW-234 (stories AW-235/236/237).
- **Model input documentation** — under WAB's inputs epic (AW-227): define the unknown **same-store-sales (SSS)** indicator (AW-239) and document all WAB inputs/sources/cadence (AW-240). The JDS twin (AW-241) sits under AW-154. One doc story per model.
- **Modeling Infrastructure initiative (AW-243)** — created the Knowledge Base epic (AW-238) + its options spike (AW-242), then promoted infrastructure to its **own Initiative** and moved both the Knowledge Base epic (AW-238) and the Data Engineering Delivery SLA (AW-226) under it.
- **Hard rule adopted:** board items (descriptions, acceptance criteria, comments, titles) **never reference the agentic diaries**. Stripped the references that had crept into AW-222/223/224/225/231 and a comment, and encoded the rule across `CLAUDE.md`, `conventions.md`, the templates, and the rest of this diary.

## Rationale

- **Per-client migration epics, not one generic upgrade epic.** AW-219 stays the cross-cutting dependency/env upgrade; each client's model migration (re-arch → QA → deploy) is its own epic so it's independently trackable and ownable — mirroring how the WAB/JDS model work is already organized.
- **Three-initiative model.** v0.17 = historical; **v0.19 = model work on the current version line**; **Modeling Infrastructure = cross-cutting capabilities that serve every model.** The Knowledge Base and the Data SLA are not pymc-marketing deliverables, so they shouldn't sit on a version line — separating them keeps v0.19 purely model work and gives infrastructure a durable home. The routing rule is recorded in [board.md](../board.md#initiative-structure).
- **No diary references on the board.** The board must stand on its own; traceability points to real artifacts (commits, notebooks, PRs) and Jira keys, never a diary session. (The diaries may still cross-reference each other — the rule is about the Jira board.)

## Follow-ups

- **AW-242** (Knowledge Base options spike) is the next concrete infra step — check whether Confluence is already sanctioned before evaluating alternatives.
- Migration epics await GPU runs: AW-231 is In Progress; the QA/deploy stories (and the whole JDS epic) are Backlog.
- Assign owners to the new Backlog stories before they're pulled.
