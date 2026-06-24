# Agentic MMM Project-Management Diary — Index

> **For AI agents**: Read [CLAUDE.md](CLAUDE.md) first (the protocol). Then [board.md](board.md) and [conventions.md](conventions.md) before any board action. Use the matching [template](templates/) before drafting an item. Pull live board state with JQL — don't treat a log entry as current truth.

## Current Focus

This diary is the canonical guide for MMM project management on the **AW — Automation workstreams** Kanban board. It encodes how the `DataScience` team writes Initiatives, Epics, and Stories, ensures every item is trackable, and runs its cadence. The board is organized under **three Initiatives** — **v0.17** (`AW-152`, historical), **v0.19** (`AW-153`, active PyMC-Marketing model work), and **Modeling Infrastructure** (`AW-243`, cross-cutting non-versioned capabilities); see the routing rule in [board.md](board.md#initiative-structure). Agents **draft by default and write to Jira only on explicit request, confirming first**, and **never reference the diaries on board items** (hard rule — see [conventions.md](conventions.md)).

## How We Work (the essentials)

- **Hierarchy:** Initiative → Epic → Story. Every Epic links to an Initiative; every Story to an Epic.
- **Spike & Bug:** Story variants (AW has no such types) — `[Spike]` / `[Bug]` prefix + purpose-built body.
- **Labels:** `DataScience` always, `Modeling` almost always, plus specifics.
- **Title prefixes:** `[Data]` `[Spike]` `[Build]` `[Deploy]` `[Delivery]` `[Bug]` `[QA]`.
- **Statuses:** Backlog → In Progress → Done. New work lands in Backlog.
- **No diary refs (hard rule):** board items never reference the agentic diaries — see [conventions.md](conventions.md).

## Reference

- [CLAUDE.md](CLAUDE.md) — agent protocol (read first)
- [board.md](board.md) — AW board reference: IDs, issue types, statuses, labels, MCP field map, JQL
- [conventions.md](conventions.md) — hierarchy, labels, prefixes, **trackability checklist**, Definition of Ready / Done
- [glossary.md](glossary.md) — PM / Jira / Kanban terms

## Templates

- [templates/initiative.md](templates/initiative.md) — durable capability / strategic theme
- [templates/epic.md](templates/epic.md) — shippable outcome under an Initiative
- [templates/story.md](templates/story.md) — single unit of work under an Epic
- [templates/spike.md](templates/spike.md) — time-boxed investigation (Story variant)
- [templates/bug.md](templates/bug.md) — defect / data discrepancy (Story variant)

## Playbooks

- [playbooks/creating-a-board-item.md](playbooks/creating-a-board-item.md) — draft → confirm → create via MCP
- [playbooks/standup.md](playbooks/standup.md) — board-walk standup
- [playbooks/backlog-grooming.md](playbooks/backlog-grooming.md) — keep the backlog ready and ordered

## Log

> Running record of PM decisions, standups, grooming, and convention changes. One topic per file: `log/YYYY-MM-DD-slug-{handle}.md` from [log/_template.md](log/_template.md).

- [2026-06-24: Migration Epics + the Modeling Infrastructure Initiative](log/2026-06-24-migration-epics-and-modeling-infrastructure-initiative-jperigo.md) — Built per-client 0.19.4 migration epics (WAB all-markets AW-230, JDS AW-234), each with `[Build]`/`[QA]`/`[Deploy]` stories; added WAB SSS (AW-239) + WAB/JDS input-documentation stories (AW-240/241); created the **Modeling Infrastructure** initiative (AW-243), off the v0.19 line, and reframed it as a **bounded MVP** with a seven-capability definition of done (reproducible env AW-246, data-eng AW-244, ML-eng AW-245, artifact versioning AW-247, data SLA AW-226, QA AW-125, knowledge base AW-238). Adopted two durable conventions: **board items never reference the diaries**, and **initiatives are bounded** (explicit DoD, reframe catch-alls as MVPs).
- [2026-06-23: v0.19 Consolidation + WAB New-Market / Enrichment Epics](log/2026-06-23-v0-19-consolidation-and-wab-epics-jperigo.md) — Created Epics AW-222 (New-Market Fit) + AW-227 (Model Inputs & Enrichment) with stories AW-223/224/225 and AW-228 (Spencer) / AW-229; added the Data Engineering SLA (AW-226); reopened AW-220; consolidated all seven active MMM epics under the v0.19 initiative (AW-153) by re-parenting AW-217/154/215; retired legacy AW-47. Codifies Spike/Bug as Story variants and the Initiative→Epic conversion mechanics.

## Related diaries

- [`../agentic-mmm-diary/`](../agentic-mmm-diary/) — MMM modeling / R&D
- [`../InsightCoreAgenticDiary/`](../InsightCoreAgenticDiary/) — InsightCore API + GUI
