# Template: Bug (Story variant)

> A defect or data discrepancy. AW has no Bug type — this is a **Story** with the `[Bug]` prefix and a reproduce/expected/actual body. Modeled on AW-221 (*QA Revenue in Client Share / Parquet Files*).

**Type:** Story · **Parent:** `<Epic key>` · **Labels:** `DataScience`, `Modeling`, `QA` (+ specific) · **Status on create:** Backlog

---

**Summary (title):** `[Bug] <what is wrong, in one line>` — e.g. *[Bug] Client transactions revenue doesn't reconcile to internal sales report*

**Description:**

```
### Description

<What's wrong, where, and the impact. For data discrepancies: which dataset, which metrics disagree, against what source of truth.>

### Steps to Reproduce

1. <load / run …>
2. <apply the standard filters / business rules …>
3. <aggregate at the same grain as the reference …>
4. <compare against the reference>

### Expected Result

<What should happen — e.g. metrics match the client's internal report within tolerance.>

### Actual Result

<What actually happens — the discrepancy, with magnitude if known.>

### Acceptance Criteria

- [ ] Root cause identified (ingestion, transform, business-rule mismatch, source data)
- [ ] Fix implemented or discrepancy explained and accepted (with tolerance)
- [ ] Reconciliation re-run confirms the metrics now match
- [ ] Fix / finding recorded (commit / PR — never a diary reference)
```

---

## Checklist before creating

- [ ] Parent Epic set; title prefixed `[Bug]`
- [ ] Reproduction steps are concrete enough for someone else to follow
- [ ] Expected vs. Actual both stated
- [ ] `DataScience`, `Modeling`, `QA` labels set
- [ ] Lands in Backlog
