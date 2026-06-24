# Agentic MMM Project-Management Diary — Instructions

This diary defines how AI agents interact with the Empower Data Science team's **Jira Kanban board** for MMM work. Follow these rules whenever you draft, create, or update a board item, or run a project-management procedure.

## The board (quick reference)

| Field | Value |
| --- | --- |
| Site | `empowermm.atlassian.net` |
| Cloud ID | `3d429359-bf0b-49b8-a372-f3c478c2f1a1` |
| Project | **AW** — Automation workstreams (software, classic) |
| Issue types | **Initiative** → **Epic** → **Story** (the only three; no native Bug or Spike) |
| Statuses | Backlog → Selected for Development → In Progress → Done |
| Team label | `DataScience` (on every MMM item) |

Full detail — IDs, the MCP field map, labels, the Spike/Bug-as-Story convention — is in [board.md](board.md). Naming, prefixes, parent-linking, and the trackability checklist are in [conventions.md](conventions.md).

## Authority: draft by default, write on request

**Default to drafting.** When asked about board work, produce a complete, ready-to-create draft from the matching [template](templates/) and show it. Do **not** create, edit, or transition a Jira issue unless the user explicitly asks you to ("create it", "add it to the board", "move it to In Progress").

**When asked to write:** show the final draft, state exactly what you're about to do (type, parent, labels, target project), and **confirm before the write**. Creating or transitioning an issue is outward-facing and visible to the whole team — treat it like a commit, not a scratch edit. One approval covers one create/transition, not a batch — confirm each batch.

Never bulk-create, bulk-transition, or delete issues without explicit, specific instruction.

## Detecting the author

Before writing any **log entry** or commit, run silently:

```
git config user.name
git config user.email
```

Populate `author` frontmatter as `Name <email>`. The email localpart is the `{handle}` used in log filenames. If either is empty, ask once, then offer to set it globally.

## Reading the board

Use `searchJiraIssuesUsingJql` with `cloudId` above. Keep result size down — the tool returns full descriptions, so:

- Request only the `fields` you need (e.g. `["summary","status","issuetype","parent","labels"]`).
- For descriptions, pass `responseContentFormat: "markdown"`.
- Large results are saved to a file; parse it with Python rather than re-querying.

Common queries live in [board.md](board.md#useful-jql).

## Drafting a board item

1. Pick the type using the hierarchy rule in [conventions.md](conventions.md): **Initiative** = a capability/strategy; **Epic** = a shippable outcome under an Initiative; **Story** = a single unit of work under an Epic. **Spike** and **Bug** are Story *variants* — a Story with the right title prefix and body (AW has no Bug/Spike issue type).
2. Copy the matching file from [templates/](templates/) and fill every section. Don't leave placeholder headings.
3. Write the title per the prefix taxonomy (`[Data]`, `[Spike]`, `[Build]`, `[Deploy]`, `[Delivery]`, `[Bug]`, `[QA]`) — see [conventions.md](conventions.md).
4. Run the **trackability checklist** in [conventions.md](conventions.md) before declaring the draft ready. An item that fails the checklist will fall off the board.

## Creating a board item (only on request)

Use `createJiraIssue` with: `cloudId`, `projectKey: "AW"`, `issueTypeName`, `summary`, `description` (with `contentFormat: "markdown"`), `parent` (Epic key for a Story, Initiative key for an Epic), and `additional_fields` for `labels` (and `priority` if not the default Medium). See the worked example in [playbooks/creating-a-board-item.md](playbooks/creating-a-board-item.md). After creating, report the new key and URL back to the user.

To move an item: `getTransitionsForJiraIssue` → `transitionJiraIssue`. To add context: `addCommentToJiraIssue`.

## Hard rule: never reference the diaries on the board

Board items — issue **descriptions, acceptance criteria, comments, and titles** — must **never reference the agentic diaries** (this PM diary or the modeling / InsightCore diaries): no session-entry names, no file paths into a diary, no "see the diary" pointers. The Kanban board stands on its own. You may reference real work artifacts (notebook filenames, commit SHAs, datasets) and other Jira keys — never a diary. Apply this when drafting, and strip any diary reference you find on an existing item. (These diaries may still cross-reference each other internally — the rule is about the **Jira board**, not these notes.)

## When to write a log entry

Write a `log/` entry (default type; use [log/_template.md](log/_template.md)) when a project-management decision is made that future agents shouldn't have to re-derive: a planning/grooming session, a change to cadence or conventions, a re-prioritization, a standup with notable blockers. Don't log routine single-issue creates — the issue itself is the record. Code/modeling work belongs in the engineering diaries, not here.

## Glossary, conventions, board reference

These are reference registers, not entries — append to them, don't template them:

- [glossary.md](glossary.md) — PM / Jira / Kanban terms. Add a term when it appears and could confuse a newcomer.
- [conventions.md](conventions.md) — the rules of the board. Amend by PR, and log the change.
- [board.md](board.md) — the factual board reference. Update if the board configuration changes (new label, status, or issue type).

## Onboarding to a session

1. Read this file (the protocol).
2. Read [board.md](board.md) and [conventions.md](conventions.md) before any board action.
3. Read the relevant [template](templates/) before drafting.
4. Read [glossary.md](glossary.md) if a term is unfamiliar.
5. Read recent `log/` entries only if the task depends on recent PM decisions.
6. Pull live board state with JQL — don't trust a stale list in a log entry as current truth.

## Committing to this diary

- Subject line names what changed and why, imperative mood, under ~70 chars (e.g. `templates: add QA story variant`).
- Body explains motivation for non-trivial changes; reference the affected file or a board key.
- Don't ask the user to review the message — write a professional one and commit.
- This repo's commit identity is the `agentdanger` account (`Courtney Perigo <jperigo@gmail.com>`).

## Rules

- One topic per log file.
- No code blocks longer than a small snippet; reference files/keys/SHAs.
- No conversation transcripts, no speculative roadmaps — only concrete next steps.
- Live Jira is the source of truth for status; this diary is the source of truth for *how* we work.
