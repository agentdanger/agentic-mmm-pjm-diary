# Agentic MMM Project-Management Diary

A persistent, agent-facing knowledge base for how the Empower Data Science team runs **MMM project management on the Jira Kanban board** (project **AW — Automation workstreams**). It tells AI agents — and humans — how to write Initiatives, Epics, and Stories that are useful, consistent, and trackable, and how we run the day-to-day cadence (standups, grooming, definition of ready/done).

This is the project-management sibling of the two engineering diaries:

- [`../agentic-mmm-diary/`](../agentic-mmm-diary/) — MMM modeling / R&D work.
- [`../InsightCoreAgenticDiary/`](../InsightCoreAgenticDiary/) — the InsightCore API + GUI reporting layer.

Where those capture *what was built and why*, this one captures *how the work gets planned, sliced, and tracked*. The board and the diaries are kept strictly separate — **board items never reference the diaries** (a hard rule; see [CLAUDE.md](CLAUDE.md) / [conventions.md](conventions.md)).

## How to use it

- **Agents**: read [CLAUDE.md](CLAUDE.md) first — it is the protocol. Then [board.md](board.md) and [conventions.md](conventions.md) before touching the board.
- **Drafting a board item**: start from the matching file in [templates/](templates/) and follow [playbooks/creating-a-board-item.md](playbooks/creating-a-board-item.md).
- **Running the cadence**: see [playbooks/](playbooks/) (standup, backlog grooming).
- **Terminology**: [glossary.md](glossary.md).

## Scope

This diary governs the **AW** project only — the canonical Kanban for MMM work. All `DataScience`-labeled Initiatives, Epics, and Stories live there. Other Empower projects (AMP, DEV, HS, JTC, POI, TR) are out of scope.

## Structure

```text
agentic-mmm-pjm-diary/
  CLAUDE.md        Agent protocol (auto-loaded by Claude Code) — read first
  README.md        This file
  INDEX.md         Front door — catalog of templates, playbooks, log entries
  glossary.md      PM / Jira / Kanban terminology
  board.md         AW board reference (IDs, issue types, statuses, labels, MCP field map)
  conventions.md   Naming, labels, title prefixes, parent-linking, trackability checklist, DoR/DoD
  templates/       One file per item type: initiative, epic, story, spike, bug
  playbooks/       Repeatable procedures: creating a board item, standup, grooming
  log/             Running log of PM decisions, standups, planning sessions
```
