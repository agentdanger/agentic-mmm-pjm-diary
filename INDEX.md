# Agentic MMM Project-Management Diary — Index

> **For AI agents**: Read [CLAUDE.md](CLAUDE.md) first (the protocol). Then [board.md](board.md) and [conventions.md](conventions.md) before any board action. Use the matching [template](templates/) before drafting an item. Pull live board state with JQL — don't treat a log entry as current truth.

## Current Focus

Standing up this diary as the canonical guide for MMM project management on the **AW — Automation workstreams** Kanban board. It encodes how the `DataScience` team writes Initiatives, Epics, and Stories, ensures every item is trackable, and runs its cadence. Agents **draft by default and write to Jira only on explicit request, confirming first.**

## How We Work (the essentials)

- **Hierarchy:** Initiative → Epic → Story. Every Epic links to an Initiative; every Story to an Epic.
- **Spike & Bug:** Story variants (AW has no such types) — `[Spike]` / `[Bug]` prefix + purpose-built body.
- **Labels:** `DataScience` always, `Modeling` almost always, plus specifics.
- **Title prefixes:** `[Data]` `[Spike]` `[Build]` `[Deploy]` `[Delivery]` `[Bug]` `[QA]`.
- **Statuses:** Backlog → In Progress → Done. New work lands in Backlog.
- **Loop:** a Story moving to Done links back to the engineering diary's session/commit.

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

- _(entries appear here as they're written)_

## Related diaries

- [`../agentic-mmm-diary/`](../agentic-mmm-diary/) — MMM modeling / R&D
- [`../InsightCoreAgenticDiary/`](../InsightCoreAgenticDiary/) — InsightCore API + GUI
