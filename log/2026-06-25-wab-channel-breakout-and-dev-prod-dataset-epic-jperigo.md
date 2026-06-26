---
date: 2026-06-25
author: Courtney Perigo <jperigo@gmail.com>
type: planning
scope: [board, initiatives]
summary: Routed the WAB video-channel breakout (OLV → CTV/OLV/YouTube) onto AW-227 as a feasibility spike plus an ML-ops build, and created a new epic (AW-256) under the Modeling Infrastructure MVP (AW-243) for separating development vs production training datasets — deliberately expanding that bounded initiative from seven to eight capability epics. Sponsorship breakout kept off-board pending analytics.
issues: [AW-227, AW-243, AW-244, AW-256, AW-257, AW-258, AW-259]
---

# WAB Channel Breakout + Dev/Prod Training-Dataset Epic

## Context

A WAB MMM channel-mapping thread (Growth Analytics + the client) proposed breaking the single OLV media driver into three — CTV, OLV, YouTube — for independent optimization, expanding the model's media drivers from 11 to 13. The owner asked where this work and its supporting infrastructure should live on the board, and to decompose it into trackable items.

## What Happened / Decided

Created one epic and three stories, all in Backlog:

- **AW-256** (Epic, under **AW-243** Modeling Infrastructure MVP) — *Development & Production Training Datasets.* A new infrastructure capability: a dev/test training dataset isolated from production so candidate input columns can be derived and model-tested without touching prod, with a documented dev → prod promotion path. Labelled like the other AW-243 infra epics (`client-shared`, `infrastructure`, `data-engineering`, no `Modeling`), plus `group-mlops` + `group-data-eng` because both disciplines own it.
- **AW-257** (`[Spike]`, under AW-256) — identify the approach for the separated dev/test vs production datasets (location, isolation, promotion path, ownership). ML-ops + data-eng.
- **AW-258** (`[Spike]`, under **AW-227** WAB Model Inputs & Enrichment) — video (OLV) breakout feasibility: spend share, live-week count, CV, channel×channel correlation, and channel×store-count correlation, nationally and by geo. Data-science work, unassigned.
- **AW-259** (`[Build]`, under AW-227) — derive the broken-out video columns into the dev training dataset and test that the 0.19.4 WAB model accepts the expanded driver count (convergence, identifiability, fit vs the v2026_3 baseline). ML-ops. Depends on AW-258 (go) and AW-257/AW-256.

Two things were deliberately **not** done: no dedicated "channel breakout" epic (the work fits AW-227's existing scope), and **no sponsorship-breakout story** was created.

## Rationale

- **Channel-breakout work belongs in AW-227, not a new epic.** AW-227's scope already names "business-requirements definition for the channel-to-grouping mapping" and "feature engineering and integration of validated inputs, with fit checked against baseline." A separate breakout epic would be sprawl. The breakout is an input change, not an architecture change, so it stays clear of AW-217 (tuning) and AW-222 (new-market fit).
- **The dev/prod dataset capability earned its own epic — and AW-243 is now an eight-epic MVP.** AW-243 was deliberately bounded as "done when its seven epics are done." The owner chose to add this as the eighth capability rather than bury it as a single story under AW-244 (ingestion), because a dev/prod training-dataset split is a standalone capability the whole modeling org needs, not just an ingestion detail. This is an intentional DoD expansion, not scope creep — recorded here so a future agent reading board.md's seven-epic framing doesn't try to "fix" it. board.md should be updated to reflect eight epics on the next reference pass.
- **Build depends on the dev dataset existing.** AW-259 derives columns into the *dev* dataset specifically — that's why it depends on AW-257/AW-256. Testing new columns against production inputs is the exact risk the new epic removes.
- **Sponsorship breakout stays off-board on purpose.** Splitting sponsorships into Genesco (contract, non-media) vs Empower (media-supported) is an analytics out-of-process workflow that must be done — including locating the data — before it's offered up as a candidate spike. Creating a board story now would imply committed work that isn't scoped or sourced yet.

## Follow-ups

- Update [board.md](../board.md) Initiative-structure note: AW-243 is now an eight-epic MVP (add the dev/prod training-dataset capability to its DoD).
- Sponsorship breakout: wait for analytics to source the data and bring a scoped proposal before drafting a spike under AW-227.
- AW-259 stays blocked until AW-258 returns a go and AW-257 recommends the dev-dataset approach.
