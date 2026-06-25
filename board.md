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

## Initiative structure

The MMM / DataScience work is organized under **three Initiatives**. The specific epics and stories under each live in Jira (the source of truth); this records the durable organizing principle — what *kind* of work belongs where.

| Initiative | Key | Holds |
| --- | --- | --- |
| **PyMC Bayesian MMM v0.17** | `AW-152` | Historical. The previous version line; only Done epics — nothing active. |
| **PyMC Bayesian MMM v0.19** | `AW-153` | Active **model work** on pymc-marketing 0.19.x — the per-client model epics (WAB, JDS) and the version migrations. |
| **Modeling Infrastructure MVP** | `AW-243` | A **bounded** set of cross-cutting, non-versioned capabilities every model needs — reproducible environment, data + ML engineering automation, artifact versioning/handoff, data SLAs, QA, knowledge base. **Done when those seven epics are done**; further infrastructure is a *later* initiative, not scope-creep here. |

**Routing rule for a new epic:** if it's *model work on the current version line*, parent it under **AW-153**; if it's *infrastructure that serves all models* (not tied to a pymc-marketing version), parent it under **AW-243**. Historical/version-specific work stays under AW-152. Per-client model migrations get their own epic under AW-153 (e.g. WAB all-markets, JDS), each decomposed into `[Build]` re-architecture / `[QA]` / `[Deploy]` stories.

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
- **Client (always, exactly one):** `client-whataburger` · `client-jdsports` · `client-sprouts` · `client-shared` (cross-client / methodology / platform). Find all of a client's work with `labels = client-<slug>`.
- **Group / discipline (the doer):** `group-data-science` · `group-mlops` · `group-data-eng` · `group-analytics` · `group-platform`. See the rule below.
- **Specific (as applicable):** `EDA`, `feature-engineering`, `report`, `deployment`, `dependency-upgrade`, `pymc-marketing`, `v0-19`, `demo-account`, `data`, `QA`, `environment`, `infrastructure`, `InsightCore`, `api`, `gui`, …

Add specific labels that match how someone would later search for the item. Reuse existing labels before inventing new ones — check with a JQL `labels` query first.

### Client and group label families (added 2026-06-25)

Two prefixed families slice the board for the two standing meeting types — per-client teams, and the data-eng / MLOps / data-science group.

- **`client-*` (exactly one per item):** the client a work item serves; `client-shared` for cross-client, methodology, infrastructure, or platform work. Initiatives that span clients are `client-shared`.
- **`group-*` (the discipline that does the work, distinct from assignee):**
  - **`group-data-science` is on EVERY item** — it is the Modeling-board membership label, so all DataScience work surfaces there. It therefore doubles as "data-science is the doer" by default.
  - Add **one** further `group-*` only when the doer is *not* data science: `group-mlops` (production ML path — env, runs, training-dataset build, artifact handoff, deploy, dependency/env upgrades), `group-data-eng` (source feeds, ingestion, data SLA, data contracts), `group-analytics` (intake / business requirements / client readouts), `group-platform` (InsightCore API + GUI app/front-end engineering).
  - So a pure data-science item carries only `group-data-science`; an MLOps deploy carries `group-data-science` + `group-mlops`. To find a discipline's own work: `labels = group-mlops` (etc.). The whole technical group at once: `labels in (group-data-science, group-mlops, group-data-eng, group-platform)`.

Note the deliberate near-collision: **`DataScience`** (the team — on everything, denotes the board) vs **`group-data-science`** (the discipline — also on everything by the membership rule). They coexist; `group-*` is the family you slice the discipline meeting with.

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

Other tools: `searchJiraIssuesUsingJql` (read), `editJiraIssue` (update fields), `getTransitionsForJiraIssue` + `transitionJiraIssue` (status moves), `addCommentToJiraIssue` (notes — never diary references).

## Useful JQL

- All MMM items: `project = AW AND labels = DataScience ORDER BY created DESC`
- A given Initiative's tree: `project = AW AND (key = AW-152 OR parent = AW-152 OR parent in (subquery of epics))` — simplest in practice is to query `parent = <epic>` per epic.
- Epics in flight: `project = AW AND issuetype = Epic AND status = "In Progress"`
- My open stories: `project = AW AND issuetype = Story AND status != Done AND assignee = currentUser()`
- Stories ready to start: `project = AW AND issuetype = Story AND status = Backlog ORDER BY created ASC`

> Reminder: request narrow `fields` and `responseContentFormat: "markdown"` to avoid oversized results.
