# Board Conventions

> The rules for writing items that are useful and trackable on the AW board. Derived from how the team already works (the `DataScience` item set) and tightened where it advances consistency. Amend by PR and record the change in `log/`.

## Issue hierarchy — pick the right level

| Level | When to use | Test |
| --- | --- | --- |
| **Initiative** | A durable capability or strategic theme that spans clients and quarters. | "Is this a *capability we're building*, not a piece of work?" Rare; you create these seldom. |
| **Epic** | A shippable outcome that needs several stories. Belongs to one Initiative. | "Does this produce a defined result and decompose into stories?" |
| **Story** | One unit of work a single owner can carry to Done in a few days. Belongs to one Epic. | "Can one person finish this and demo it?" If it needs sub-work, it's probably an Epic. |

**Every Epic links to an Initiative. Every Story links to an Epic.** A parentless Epic or Story is the #1 way work falls off the board — Jira hierarchy reports and roadmaps won't show it.

### Spike and Bug are Story variants

AW has no Bug or Spike issue type (see [board.md](board.md)). Express them as Stories:

- **Spike** — time-boxed investigation that ends in a decision/recommendation, not shipped code. Title prefix `[Spike]`; body uses [templates/spike.md](templates/spike.md) (questions → go/no-go).
- **Bug** — a defect or data discrepancy. Title prefix `[Bug]`; body uses [templates/bug.md](templates/bug.md) (Steps to Reproduce / Expected / Actual).

## Title prefix taxonomy

Prefix the Story summary with the kind of work, so the backlog reads as a workflow at a glance:

| Prefix | Meaning |
| --- | --- |
| `[Data]` | Acquire, fix, or stand up a data source / feed |
| `[Spike]` | Time-boxed investigation / EDA ending in a recommendation |
| `[Build]` | Implement a feature, control, or model change |
| `[Deploy]` | Ship artifacts to an API, GUI, or environment |
| `[Delivery]` | Produce a client-facing readout / deck |
| `[Bug]` | Fix a defect or data discrepancy |
| `[QA]` | Validate / reconcile data or model outputs |

Initiatives and Epics use plain descriptive titles (no prefix). A Story may legitimately have no prefix if none fits, but prefer one.

## Labels

Required on every item: **`DataScience`**. Add **`Modeling`** unless the work genuinely isn't modeling-adjacent. Then add specific labels matching how the item would be searched later (`EDA`, `feature-engineering`, `deployment`, `dependency-upgrade`, `report`, `QA`, client/version tags like `pymc-marketing` / `v0-19`). Reuse existing labels — query `labels` before coining a new one.

## Description quality

- Use clean Markdown headings and `- [ ]` checkboxes. **Do not wrap the whole description in a ` ```markdown ` fence** — some older items did; it renders as a code block, not formatted text.
- Every **Story** has a `### Description` and `### Acceptance Criteria` (checkbox list). Acceptance criteria are the contract — they define Done for that story.
- Every **Epic** states Goal, Context/Why-now, Scope (In / Out), Success criteria, and Risks & dependencies.
- Write acceptance criteria as verifiable outcomes ("Model builds and samples without divergences"), not activities ("work on the model").

## Trackability checklist (Definition of Ready)

Before a draft is "ready" — i.e. before it's created, or before a Backlog item is pulled into In Progress — confirm **all** of:

- [ ] Correct **issue type** for its hierarchy level
- [ ] **Parent** set (Story → Epic; Epic → Initiative)
- [ ] **`DataScience`** label present (+ domain + specific labels)
- [ ] **Title** follows the prefix taxonomy (Stories)
- [ ] **Description** filled from the template — no placeholder headings
- [ ] **Acceptance criteria** present and verifiable (Stories)
- [ ] **Owner** identified (assignee) if it's being started
- [ ] Lands in **Backlog** (new work) — not created straight into In Progress

An item that fails any box is not ready and will be hard to track.

## Definition of Done

A Story is Done when:

- [ ] All acceptance criteria are checked
- [ ] Output is where it should live (artifact deployed, dataset landed, deck delivered, fix merged)
- [ ] The work is **linked back to the engineering diary** — a comment on the issue pointing to the session entry or commit SHA in `../agentic-mmm-diary/` or `../InsightCoreAgenticDiary/`
- [ ] Status moved to **Done** (don't leave finished work In Progress)

An Epic is Done when its stories are Done and its success criteria are met. An Initiative is rarely "Done" — it's an ongoing capability.

## WIP and flow

- Keep work flowing left-to-right; finish before starting. Prefer pulling the oldest ready Story over starting new ones.
- Don't move a Story to In Progress until someone is actually working it (status should reflect reality).
- If a Story is blocked, say so in a comment naming the blocker and move on — don't silently leave it In Progress.
