---
date: 2026-07-13
author: Courtney Perigo <jperigo@gmail.com>
type: planning
scope: [board]
summary: Tracked the WAB v2026_5 promotion and the work it surfaced onto the AW board. Under New-Market Fit (AW-222): the v2026_5 [Build] (AW-284, Done) and [Deploy] (AW-285, Anagh); a [Bug] for the Greensboro transactions-input truncation that blocks the deploy (AW-286, Anagh); and a [Spike] to choose the production born-market bound policy from the geoscale candidates (AW-287, Courtney), gated on the data fix. Flagged AW-286 onto the WAB New-Unit-Listing automation (AW-274) as an impediment. Opened a client data-delivery SLA pair under the Data Engineering Delivery SLA epic (AW-226): WAB (AW-288, Jon, relates-to AW-240) and JDS (AW-289, Victoria, relates-to AW-241).
issues: [AW-222, AW-284, AW-285, AW-286, AW-287, AW-274, AW-226, AW-288, AW-289, AW-240, AW-241]
---

# v2026_5 Promotion + New-Market Data Tracking

## Context

The WAB v2026_5 model (per-geo scaling restoration) was promoted to the production notebook, run, and assessed against the live API. The assessment surfaced a data-integrity issue and a deliberate modeling-policy decision, and the recurring feed problems argued for formalizing data SLAs. All of it needed board representation.

## What Happened / Decided

Under **New-Market Fit (AW-222)**:

- **AW-284 `[Build]`** — v2026_5 (per-geo scaling + exact-center priors + identification gate + growth-confounded key). Transitioned **Done** with an AC-to-evidence completion comment.
- **AW-285 `[Deploy]`** — run the promotion and drop the artifact package. Assigned **Anagh**, Backlog.
- **AW-286 `[Bug]`** — Greensboro transactions input truncates at 2025-10-21 (only market affected; live API has it through 2026-06). Assigned **Anagh**. **Blocks a clean AW-285 deploy** for Greensboro and **gates AW-287**.
- **AW-287 `[Spike]`** — select the production born-market bound policy from the geoscale candidates (unbounded v2026_5 vs a bounds overlay). Assigned **Courtney**. Its clean evaluation is gated on the AW-286 data fix (retrain on refreshed input).

Cross-epic:

- Commented on **AW-274** (WAB New-Unit-Listing Automation, under Data-Eng ingestion AW-244) flagging **AW-286** as a concrete instance of the silent market drop-off the automation must catch — its store-capture check should extend to the DMA/market grain.
- Opened a client **data-delivery SLA** pair under **AW-226** (Data Engineering Delivery SLA): **AW-288** (WAB, **Jon**, relates-to his input-inventory AW-240) and **AW-289** (JDS, **Victoria**, relates-to her input-inventory AW-241). Each turns an existing input catalog into an agreed, monitored delivery guarantee.

## Rationale

- The Greensboro truncation is not a one-off — it is a **silent market drop-off** (likely a DMA rename in the feed) that no gate currently catches, so it warranted a bug that both blocks the deploy and drives a durable continuity check (into AW-274 and the SLAs), not just a quiet data patch.
- The born-market bounds are a **business/modeling judgment**, not a metric to optimize: crediting new/expansion markets meaningfully (Charlotte ~20%) vs. forward accuracy in the tiny gated markets (Topeka), where the two cannot both hold. That deserves a spike ending in a go/no-go, not an ad-hoc pick — hence AW-287.
- The SLA stories mirror the existing input-documentation pair (AW-240/241, same owners) so each owner sees the catalog and the guarantee together; the WAB/JDS split keeps ownership clear while both cite the same continuity gate.

## Follow-ups

- AW-286 resolved before the AW-285 drop (else Greensboro regresses to stale data on cutover).
- AW-287 evaluation runs after AW-286 (retrain on the refreshed input for clean P6 reads).
- SLA definition (AW-288/289) developed alongside the input inventories with Data Engineering.
