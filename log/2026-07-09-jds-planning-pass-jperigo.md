---
date: 2026-07-09
author: Courtney Perigo <jperigo@gmail.com>
type: planning
scope: [board]
summary: JDS planning pass — Victoria assigned to plan the four empty JDS epics (AW-251/252/253/254, sequenced 253 → 251 → 254 → 252); AW-253 built out first with a discovery-first pattern for unknown candidates — parallel supply (AW-279 taxonomy inventory) and demand (AW-280 business requirements) stories feeding a single pre-staged-but-blocked batch identifiability spike (AW-281). Structural rulings — one batch spike with per-candidate verdicts (not a spike per candidate), and approved breakouts feed ONE downstream implementation epic (not one epic per breakout).
issues: [AW-251, AW-252, AW-253, AW-254, AW-279, AW-280, AW-281]
---

# JDS Planning Pass — Four Empty Epics, AW-253 Built Out Discovery-First

## Context

A JDS board inventory (35 items: 6 epics, 29 stories) found the v2 enriched line effectively shipped (AW-154 at 19/22 Done, AW-234 migration Done) and four epics from the 2026-06-24 board review still empty, unassigned placeholders: AW-251 Ecommerce Revenue, AW-252 New-vs-Repeat Buyer, AW-253 Channel-Tactic Breakouts, AW-254 Brand Equity Signal. The owner wanted a data scientist planning them into viable production-feature pipelines.

## What Happened / Decided

- **Victoria plans the four epics.** She ran nearly every JDS discovery story in the v2 cycle; Anagh is loaded with AW-277 + the AW-246 workspace rollout. Owner assigned AW-253 directly; the other three still need the assignment applied.
- **Sequencing recommendation: AW-253 → AW-251 → AW-254 → AW-252.** 253 has the strongest precedent (the WAB video breakout shipped end-to-end) and data in hand; 251 is high value but **gated on AW-221** (revenue QA — don't fit a new revenue target on unreconciled data); 254 has data but the hardest identification (spike needs explicit kill criteria); 252 has the highest data risk (customer-identity at weekly-geo grain).
- **AW-253 built out discovery-first** — the breakout candidates are unknown, so the epic starts one stage earlier than the WAB precedent: **AW-279** `[Data]` taxonomy inventory (supply — what the feeds can split) and **AW-280** `[Data]` business requirements (demand — what would change a decision) run in parallel; their intersection scopes **AW-281** `[Spike]` identifiability go/no-go. AW-281 is **pre-staged in Backlog but blocked** — scope-locking from the AW-279×AW-280 handoff is its first AC, and it must not be pulled to In Progress before the list exists. The epic's Approach section records the plan.
- **One batch spike, not a spike per candidate.** Identifiability is a joint property — candidates compete for the same per-(channel, geo) parameter budget, so the verdict must cover the recommended *combination*; the checks share one harness; and the WAB feasibility spike (AW-258) handled a three-way split as one story. Cap: top ~5 prioritized candidates, remainder logged as deferred; "not-yet" verdicts name the missing data and its owner.
- **Approved breakouts feed ONE implementation epic** (`[Build]` per breakout + shared refit/`[QA]`-vs-baseline/`[Deploy]`), created when the go/no-go lands — **not** one epic per breakout. Breakouts ship together as the next model version (one refit, one artifact, one reporting-contract change), and the 2026-06-25 WAB routing decision already rejected dedicated breakout epics. AW-253's out-of-scope line was amended accordingly. Exception reserved: a breakout needing its own data feed or experiment cycle splits out rather than holding the batch hostage.

## Rationale

Story-generation discipline drove every call: only work that passes Definition of Ready gets created (the spike's ACs are verifiable today because scope-locking is itself the first criterion); build/QA/deploy tails are not pre-populated for features that might die at feasibility; and the epic body carries the full arc so the plan is visible without speculative backlog. The demand story (AW-280) exists because a breakout nobody budgets against is model complexity for nothing — every candidate must name the decision it informs.

## Follow-ups

- Assign AW-251, AW-252, AW-254 to Victoria (owner to confirm; only AW-253 is assigned).
- Build out the other three epics' discovery pairs per the sequencing above (AW-251 waits on AW-221's resolution).
- Board hygiene from the inventory, still open: AW-216 is In Progress but unassigned (assign or return to Backlog); decide whether AW-154's three open stories (AW-155, AW-221, AW-241) block the epic or move so it can close.
