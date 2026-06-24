# Playbook: Backlog grooming

> Keep the backlog ordered, ready, and honest. Run periodically (e.g. weekly) so the top of Backlog is always the next thing worth pulling.

## When to use

On a regular cadence, and whenever the backlog has drifted — new epics landed, priorities shifted, or stories have gone stale.

## Prerequisites

- Pull the open backlog: `project = AW AND status = Backlog ORDER BY created ASC` (narrow `fields`, markdown descriptions).
- Have [conventions.md](../conventions.md) open for the trackability checklist and hierarchy rules.

## Steps

1. **Parentless sweep** — find Stories/Epics with no parent (`project = AW AND issuetype = Story AND parent is EMPTY`). Attach each to its Epic/Initiative, or close it. Parentless work is invisible work.
2. **Readiness pass** — for the top items, run the **trackability checklist**. Anything missing AC, labels, or a clear description gets fixed or dropped back down the order.
3. **Right-size** — a "Story" that's really several stories gets split or promoted to an Epic; a stale Spike whose decision is moot gets closed.
4. **Re-order** — sort so the highest-value, ready work is at the top. Record any non-obvious prioritization rationale in a `log/` entry.
5. **De-dupe & retire** — close duplicates and won't-do items with a one-line rationale (e.g. a no-go from a Spike). Don't let dead work linger in Backlog.
6. **Label hygiene** — ensure `DataScience` (+ domain + specific) labels are present and reuse existing labels rather than coining near-duplicates.

## Verification

- Top-of-backlog items all pass the Definition of Ready.
- No parentless Stories/Epics remain.
- Closed items have a stated reason.

## Output

A `log/` entry (type: grooming) when prioritization changed materially or conventions were applied at scale — capture what moved and why.

## Troubleshooting

- **Backlog keeps growing** → it's a wish-list, not a plan; aggressively close won't-dos and keep only what's genuinely next.
- **Can't tell an item's value** → it's not ready; add the missing context or drop it.
