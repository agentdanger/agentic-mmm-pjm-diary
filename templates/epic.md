# Template: Epic

> Use for a shippable outcome that groups several stories. **Must link to an Initiative.** No title prefix. Body goes in the Jira **description** (Markdown, no surrounding code fence). Modeled on AW-154 and AW-217.

**Type:** Epic · **Parent:** `<Initiative key, e.g. AW-152>` · **Labels:** `DataScience`, `Modeling` (+ specific) · **Status on create:** Backlog

---

**Summary (title):** `<Outcome name>` — e.g. *WAB MMM: Model Quality Refinement*

**Description:**

```
### Goal

<1–2 sentences: the outcome this epic delivers and the quality/defensibility it adds. State what is explicitly NOT changing if that scopes it, e.g. "without changing the model architecture, channel set, or input data.">

### Context / Why now

<Why this matters now. Current state, baseline metrics, the headroom or gap this closes.>

### Scope

* **In scope:**
    * <workstream / change 1>
    * <workstream / change 2>
* **Out of scope:**
    * <explicitly excluded; where it goes instead, e.g. "deferred to v3">

### Success criteria

* <verifiable outcome 1 — e.g. priors re-derived from data and documented>
* <verifiable outcome 2 — e.g. validation metrics documented (R², MAPE, coverage)>
* <verifiable outcome 3 — e.g. readout delivered>

### Risks and dependencies

* <risk or dependency 1 — data arrival, identifiability, parameter count vs. data, etc.>
* <risk or dependency 2>
```

---

## Checklist before creating

- [ ] Parent Initiative set
- [ ] Decomposes into stories (if it's one unit of work, it's a Story)
- [ ] Success criteria are verifiable, not activities
- [ ] In/Out scope stated — out-of-scope items say where they go instead
- [ ] `DataScience` (+ `Modeling` + specific) labels set
- [ ] Lands in Backlog
