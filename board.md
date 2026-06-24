# AW Board Reference

> The factual reference for the **AW — Automation workstreams** Kanban board. Update this file when the board configuration changes (a new label becomes standard, a status is added, an issue type is introduced). Conventions for *how to use* the board live in [conventions.md](conventions.md); this is the *what exists*.

## Connection

| Field | Value |
| --- | --- |
| Site | `empowermm.atlassian.net` |
| Cloud ID | `3d429359-bf0b-49b8-a372-f3c478c2f1a1` |
| Project key | `AW` |
| Project name | Automation workstreams |
| Project type | software, classic (company-managed) |

## Issue types (hierarchy)

AW exposes exactly three issue types. There is **no Bug, Spike, or Sub-task type**.

| Type | Jira ID | Hierarchy level | Parent | Use for |
| --- | --- | --- | --- | --- |
| **Initiative** | `10038` | 2 | none | A durable capability or strategic theme (e.g. AW-152 *PyMC Bayesian MMM v0.17*) |
| **Epic** | `10000` | 1 | Initiative | A shippable outcome that groups stories (e.g. AW-219 *Upgrade PyMC-Marketing to v0.19*) |
| **Story** | `10039` | 0 | Epic | A single trackable unit of work (e.g. AW-220 *Upgrade demo account…*) |

**Spike** and **Bug** are modeled as **Story variants** — a Story with the matching title prefix and body template (see [templates/spike.md](templates/spike.md), [templates/bug.md](templates/bug.md)). Example of a bug-as-Story already on the board: AW-221. If the team ever wants true Bug/Spike issue types, a Jira admin must add them to the AW issue-type scheme — that is a board-config change, not something an agent can do.

## Statuses (workflow)

`Backlog` → `Selected for Development` → `In Progress` → `Done`

New items land in **Backlog**. **Selected for Development** stages groomed, ready work pulled for the next cycle but not yet started. Move to **In Progress** only when work actually starts (respect WIP — see [conventions.md](conventions.md)). Move to **Done** only when the Definition of Done is met.

Transition IDs (for `transitionJiraIssue`): Backlog `11`, Selected for Development `21`, In Progress `31`, Done `41`. Note: there is **no Cancelled / Won't-Do** state — retire a superseded item by moving it to **Done** with a comment explaining it's superseded, not completed.

## Priority

Default is **Medium** — and in practice nearly everything stays Medium. Raise priority only with a stated reason; don't set it reflexively.

## Labels

Labels are how items are grouped and found (AW has no separate component taxonomy in use). Layered convention:

- **Team (always):** `DataScience`
- **Domain (almost always):** `Modeling`
- **Specific (as applicable):** `EDA`, `feature-engineering`, `report`, `deployment`, `dependency-upgrade`, `pymc-marketing`, `v0-19`, `demo-account`, `data`, `QA`, …

Add specific labels that match how someone would later search for the item. Reuse existing labels before inventing new ones — check with a JQL `labels` query first.

## MCP field map (creating / editing via tools)

`createJiraIssue` parameters → Jira fields:

| Param | Value / notes |
| --- | --- |
| `cloudId` | `3d429359-bf0b-49b8-a372-f3c478c2f1a1` |
| `projectKey` | `"AW"` |
| `issueTypeName` | `"Initiative"` \| `"Epic"` \| `"Story"` |
| `summary` | Title, with prefix taxonomy applied |
| `description` | Body; pass `contentFormat: "markdown"` |
| `parent` | Epic key for a Story; Initiative key for an Epic |
| `additional_fields` | `{ "labels": ["DataScience","Modeling", …] }`; add `{ "priority": {"name":"High"} }` only if non-default |

Other tools: `searchJiraIssuesUsingJql` (read), `editJiraIssue` (update fields), `getTransitionsForJiraIssue` + `transitionJiraIssue` (status moves), `addCommentToJiraIssue` (notes / diary back-links).

## Useful JQL

- All MMM items: `project = AW AND labels = DataScience ORDER BY created DESC`
- A given Initiative's tree: `project = AW AND (key = AW-152 OR parent = AW-152 OR parent in (subquery of epics))` — simplest in practice is to query `parent = <epic>` per epic.
- Epics in flight: `project = AW AND issuetype = Epic AND status = "In Progress"`
- My open stories: `project = AW AND issuetype = Story AND status != Done AND assignee = currentUser()`
- Stories ready to start: `project = AW AND issuetype = Story AND status = Backlog ORDER BY created ASC`

> Reminder: request narrow `fields` and `responseContentFormat: "markdown"` to avoid oversized results.
