# Playbook: Creating a board item

> How an agent takes a request and turns it into a trackable AW item — drafting always, creating only on explicit request. This is the core agentic loop for this diary.

## When to use

Any time someone wants new work on the board: "add a story for X", "we need an epic to cover Y", "log a bug for Z". Also when grooming surfaces a missing item.

## Prerequisites

- Read [board.md](../board.md) and [conventions.md](../conventions.md).
- Know the **parent**: a Story needs its Epic; an Epic needs its Initiative. If unknown, find it with JQL before drafting (`project = AW AND issuetype = Epic` etc.).

## Steps

1. **Choose the level** — Initiative / Epic / Story (or Story variant Spike/Bug) using the hierarchy test in [conventions.md](../conventions.md).
2. **Draft from the template** — copy the matching file in [templates/](../templates/), fill every section, apply the title prefix.
3. **Run the trackability checklist** (Definition of Ready) in [conventions.md](../conventions.md). Fix anything that fails.
4. **Show the draft to the user** and stop. This is the default end state — do not create yet.
5. **On explicit "create it"**: restate what you're about to do (type, parent, labels, project AW), confirm, then call `createJiraIssue`:
   - `cloudId: 3d429359-bf0b-49b8-a372-f3c478c2f1a1`, `projectKey: "AW"`
   - `issueTypeName`, `summary`, `description` with `contentFormat: "markdown"`
   - `parent: "<Epic or Initiative key>"`
   - `additional_fields: { "labels": ["DataScience","Modeling", …] }`
6. **Report back** the new key and URL. If the item is starting immediately, only then transition it (`getTransitionsForJiraIssue` → `transitionJiraIssue`) — otherwise leave it in Backlog.

## Verification

- The new item appears under its parent (query `parent = <key>` or open the key).
- Labels, type, and parent match the draft.
- It's in **Backlog** unless work has genuinely started.

## Troubleshooting

- **Item doesn't show on the roadmap/board hierarchy** → missing or wrong `parent`. Fix with `editJiraIssue`.
- **Created at the wrong level** → there's no in-place type change via these tools; comment, close as duplicate, and recreate at the right level (rare — that's what the draft-and-confirm step prevents).
- **Label sprawl** → reuse existing labels; query `labels` first.
- **Oversized read results** when finding the parent → narrow `fields`, use `responseContentFormat: "markdown"`, parse the saved file.
