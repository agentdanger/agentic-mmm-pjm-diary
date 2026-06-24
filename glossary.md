# Glossary

> Project-management, Jira, and Kanban terms used across this diary. MMM modeling terminology lives in the engineering diary's [glossary](../agentic-mmm-diary/glossary.md). Add a term when it appears in a template, playbook, or log entry and could confuse a newcomer. Keep definitions terse (1–3 sentences). Cross-link related terms in **bold**.

## A

- **Acceptance Criteria (AC)** — The verifiable conditions that define when a **Story** is complete. Written as a `- [ ]` checkbox list; they are the contract for the work. Distinct from the **Definition of Done**, which applies to *every* story.

## B

- **Backlog** — The first board status; where new, ready-but-not-started work waits. Ordered so the top is the next thing to pull.
- **Blocker** — Anything preventing a **Story** from progressing (missing data, external dependency, decision needed). Surface blockers in the **standup** and as an issue comment; don't leave blocked work silently In Progress.

## D

- **Definition of Done (DoD)** — The standard conditions every **Story** must meet to be Done, beyond its own **acceptance criteria** (output shipped, where it landed recorded, status moved — never a diary reference). See [conventions.md](conventions.md).
- **Definition of Ready (DoR)** — The conditions an item must meet before it can be created or pulled into work. Encoded as the **trackability checklist** in [conventions.md](conventions.md).

## E

- **Epic** — A shippable outcome that groups several **Stories** and belongs to one **Initiative**. Hierarchy level 1 in AW. Carries Goal, Scope, Success criteria, Risks.

## H

- **Hierarchy** — The Initiative → Epic → Story parent chain. Keeping parent links intact is what makes work show up in Jira roadmaps and hierarchy reports.

## I

- **Initiative** — The top hierarchy level (level 2 in AW): a durable capability or strategic theme spanning clients and quarters (e.g. "PyMC Bayesian MMM v0.19").

## J

- **JQL** — Jira Query Language. Used via the `searchJiraIssuesUsingJql` MCP tool to read the board. See [board.md](board.md#useful-jql).

## K

- **Kanban** — A flow-based work-management method: a board with columns (**Backlog → In Progress → Done**), pull-based work, and **WIP** limits, with no fixed sprints.

## P

- **Parent link** — The field connecting a **Story** to its **Epic**, or an **Epic** to its **Initiative**. Required on every Story and Epic.
- **Prefix taxonomy** — The `[Data]`/`[Spike]`/`[Build]`/`[Deploy]`/`[Delivery]`/`[Bug]`/`[QA]` Story-title prefixes that label the kind of work. See [conventions.md](conventions.md).

## S

- **Spike** — A time-boxed investigation (often EDA) that ends in a decision or recommendation rather than shipped code. Modeled as a **Story** with the `[Spike]` prefix (AW has no Spike type).
- **Standup** — The recurring sync where the team walks the board, checks flow, and surfaces blockers. See [playbooks/standup.md](playbooks/standup.md).
- **Story** — A single unit of work one owner can carry to Done, belonging to one **Epic**. Hierarchy level 0. **Bug** and **Spike** are Story variants.

## T

- **Trackability checklist** — The Definition-of-Ready checklist that ensures a new item appears on the board and can be followed (correct type, parent, labels, AC). See [conventions.md](conventions.md).

## W

- **WIP (Work In Progress)** — The amount of work in the In Progress column at once. Kept low so items finish before new ones start; flow over utilization.
