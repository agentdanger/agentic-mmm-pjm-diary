# Playbook: Standup

> How we run the recurring sync. Kanban-style **board walk** (flow-focused), not a round-robin status recitation. An agent can prepare the standup, run the board pull, and draft the notes.

## When to use

The team's regular cadence (default: a short daily async check-in, with a live walk as needed). Use it to keep work flowing and surface blockers early — not to assign blame or replan the roadmap.

## Prerequisites

- Live board state via JQL (don't rely on a stale list):
  - In flight: `project = AW AND status = "In Progress" ORDER BY updated DESC`
  - Blocked / stale: In Progress items not updated recently, or with a blocker comment
  - Ready to pull: `project = AW AND issuetype = Story AND status = Backlog ORDER BY created ASC`

## Steps — walk the board right to left

1. **Done since last time** — what moved to Done? Confirm each is genuinely done (acceptance criteria checked, output shipped). Celebrate, then move on.
2. **In Progress** — for each item, focus on *flow*: is it moving? Is anything **blocked**? Who needs what to unblock it? Note blockers as issue comments.
3. **WIP check** — is too much in progress at once? If so, the team finishes before pulling new work.
4. **Ready to start** — only if there's capacity, pull the top Backlog story. Confirm it passes the trackability checklist (Definition of Ready) before it goes In Progress.
5. **Misses** — any In-Progress work with no parent, no AC, or stale > a few days gets fixed or re-groomed.

## Verification

- Every In Progress item has a clear next action or a named blocker.
- Nothing is sitting In Progress that nobody is working.
- New pulls are Ready (pass the checklist).

## Output

If the standup produced decisions or notable blockers, write a `log/` entry (type: standup) capturing: what moved, current blockers + owners, and any re-prioritization. Routine standups with nothing notable don't need a log entry.

## Troubleshooting

- **Everything's In Progress, nothing's Done** → WIP too high; stop starting, start finishing.
- **Same blocker every standup** → escalate it as its own issue or a comment to the blocker's owner; don't re-note it indefinitely.
- **Status doesn't match reality** → fix the board during the walk so it stays the source of truth.
