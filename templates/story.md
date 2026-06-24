# Template: Story

> The default unit of work — one owner, carried to Done in a few days. **Must link to an Epic.** Title takes a prefix from the taxonomy. Body goes in the Jira **description** (Markdown, no surrounding code fence). Modeled on AW-157, AW-163, AW-220.

**Type:** Story · **Parent:** `<Epic key, e.g. AW-217>` · **Labels:** `DataScience`, `Modeling` (+ specific) · **Status on create:** Backlog

---

**Summary (title):** `[<Prefix>] <imperative outcome>` — e.g. *[Build] Add product launch controls to MMM*

Prefixes: `[Data]` `[Spike]` `[Build]` `[Deploy]` `[Delivery]` `[Bug]` `[QA]` (see [conventions.md](../conventions.md)). For a Spike or Bug, use [spike.md](spike.md) / [bug.md](bug.md) instead — they have purpose-built bodies.

**Description:**

```
### Description

<2–4 sentences: what to do and why, with enough context for the owner to start. Reference the spike, dataset, or epic it follows from. Name the concrete inputs/outputs.>

### Acceptance Criteria

- [ ] <verifiable outcome 1>
- [ ] <verifiable outcome 2>
- [ ] <verifiable outcome 3>
- [ ] <... include "fit/validation compared to baseline" or "documented in glossary" where relevant>
```

---

## Checklist before creating

- [ ] Parent Epic set
- [ ] Title has a taxonomy prefix
- [ ] One owner can finish it (otherwise split or promote to Epic)
- [ ] Acceptance criteria are verifiable outcomes, not activities
- [ ] `DataScience` (+ `Modeling` + specific) labels set
- [ ] Lands in Backlog
- [ ] (At Done) linked back to the engineering diary session/commit
