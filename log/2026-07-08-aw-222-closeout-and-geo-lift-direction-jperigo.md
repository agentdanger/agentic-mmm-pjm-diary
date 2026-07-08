---
date: 2026-07-08
author: Courtney Perigo <jperigo@gmail.com>
type: decision
scope: [board]
summary: Reconciled the AW-222 tree with the v2026_4 promotion — closed AW-260 (activation-gated baseline, shipped in the v2026_4 production notebook), created AW-277 [Deploy] for Anagh to take the notebook to production, and adopted a direction change on the residual confounded markets — geo-lift experiments (AW-278 design spike) replace the exhausted observational program. AW-225 (iteration-over-iteration fit tracking) stays open.
issues: [AW-222, AW-225, AW-260, AW-277, AW-278]
---

# AW-222 Close-Out Pass + the Geo-Lift Direction Change

## Context

The WAB v2026_4 production notebook was promoted in R&D on 2026-07-08 (mmm-wab `40cdf7d`/`8322135`), which left the AW-222 *New-Market Fit* tree behind reality: the intercept-fix build was still In Progress and nothing tracked the promotion run or the path for the markets the model provably cannot attribute.

## What Happened / Decided

- **AW-260 → Done.** The activation-gated baseline shipped in `PyMC_Marketing_MMM_WAB_v2026_4_transactions_allDMA_production.ipynb`; the completion comment maps every acceptance criterion to where it landed, including the maturity-exposure keep/drop decision (dropped) and the `active_gate` InsightCore registry entry (InsightCoreAPI `42b1401`).
- **AW-277 created** — `[Deploy] Promote the WAB v2026_4 all-DMA model to production`, under AW-222, assigned to Anagh (MLOps): fresh pull → Run All → `artifact_version: 2` package → landing-dir drop → post-drop verification. Backlog until he picks it up.
- **AW-225 stays open.** The owner explicitly kept the iteration-over-iteration expansion-fit scorecard running under AW-222.
- **Direction change: geo-lift experiments are now the AW-222 dial-in path.** Created **AW-278** — `[Spike] Design a geo-lift experiment to measure media ROI in store-growth-confounded WAB markets` — one spike covering both confounded cohorts (the 9 expansion/born markets and the grew-in-place Kansas City class), per the owner's call to keep the two tests under one design story. Backlog, unassigned.
- Housekeeping: the owner corrected AW-264's labels/prefix directly.

## Rationale

The 2026-06-29 direction was to solve new-market fit observationally and it partly worked: the activation-gated baseline fixed the *level* problem (born-market holdout 99–160% → 7–22%) and is now production. But the *media attribution* problem inside store-growth markets survived every observational attack — eight expansion architectures (v2026_5–v2026_8e), then the gateramp and ctlexposure control designs on the v2026_4 line, each reverted with documented mechanisms. The earlier owner position (2026-06-16) rejecting "an experiment is the only path" was contingent on an observational route existing; with that route exhausted by evidence, adopting the geo-lift design spike is the consistent next move, not a reversal. The reporting-layer media gate (national/tier fallback) remains the standing treatment until an experiment reads out, which is why AW-278 is a design-and-go/no-go spike — the client decides on cost vs. the decision it unlocks before any execution stories exist.

One spike rather than two: both cohorts share the machinery (matched controls, power analysis, measurement plan) and the output is a single client recommendation; execution, if greenlit, splits per cohort naturally.

## Follow-ups

- When Anagh starts AW-277, move it to In Progress (status reflects reality).
- If AW-278's design gets a client go, create per-cohort execution stories under AW-222 (or a dedicated epic if the experiment outgrows story scope).
- AW-222 closes only after AW-277 ships and the owner decides whether AW-225 and AW-278 live on under it or move.
