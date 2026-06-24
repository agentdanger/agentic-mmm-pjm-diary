# Template: Spike (Story variant)

> A time-boxed investigation (often EDA) that ends in a **decision/recommendation**, not shipped code. AW has no Spike type — this is a **Story** with the `[Spike]` prefix. Modeled on AW-156, AW-159–162.

**Type:** Story · **Parent:** `<Epic key>` · **Labels:** `DataScience`, `Modeling`, `EDA` (+ specific) · **Status on create:** Backlog

---

**Summary (title):** `[Spike] <question / feature under investigation>` — e.g. *[Spike] Product launch feature EDA*

**Description:**

```
### Description

<What we're investigating and why. Frame the key questions explicitly, e.g.: How do we define "<thing>" from the data? What's the right granularity/encoding? Is there enough variance to be useful? How correlated is it with media timing (confounding risk)?>

### Acceptance Criteria

- [ ] <thing> is operationally defined from the data (criteria documented)
- [ ] Mapped to the weekly MMM timeline
- [ ] Coverage / variance assessed (enough on-off signal to be useful?)
- [ ] Correlation / confounding risk assessed and documented
- [ ] Feature-encoding recommendation documented (binary, count, weighted, decay, …)
- [ ] **Go / no-go recommendation** with rationale
- [ ] If go: feature-engineering approach documented for the downstream [Build] story
- [ ] If no-go: downstream build story closed as won't-do with rationale
```

---

## Checklist before creating

- [ ] Parent Epic set; title prefixed `[Spike]`
- [ ] Time-box stated or understood (a spike is bounded)
- [ ] AC end in a **decision** (go/no-go), not just "explored"
- [ ] A follow-on `[Build]` story exists or is implied by the go path
- [ ] `DataScience`, `Modeling`, `EDA` labels set
- [ ] Lands in Backlog
