---
date: 2026-07-18
author: Courtney Perigo <jperigo@gmail.com>
type: planning
scope: [board]
summary: Owner promoted the totalshare spec as v2026_5 (second re-point; AtoSscale3 rejected, archived as exp2026_10) — which made the in-flight deploy story AW-285 dangerous: it was In Progress, assigned to Anagh, and instructed him to drop the now-rejected 2026-07-15 artifact package. Created AW-292 ([Deploy] the re-pointed v2026_5, full artifact replacement, Anagh, under AW-222) and posted a STOP comment on AW-285 directing it to Done-as-superseded. AW-292 carries the model_version collision warning (the served AtoSscale3 artifact and the replacement share `WAB_v2026_5_allDMA`; `generated_at_utc` is the only discriminator, so the drop must be a full replacement) plus the stale saturation-JSON glob trap and the ~8 GB cache/RAM check inherited from AW-285.
issues: [AW-292, AW-285, AW-222, AW-287, AW-286]
---

# v2026_5 Re-Point: Deploy Supersession (AW-285 → AW-292)

## Context

The owner promoted the totalshare candidate to production on 2026-07-17, accepting the known Atlanta holdout regression, and ruled the AtoSscale3 promotion rejected and not counted as deployed — so `v2026_5` was re-pointed for the second time (mmm-wab `e915d00`; rename map in `archive_models/NAMING.md`). This left the board actively wrong: AW-285 was In Progress with Anagh, telling him to drop the rejected AtoSscale3 package. This is the same failure mode AW-285 itself was rewritten for on 2026-07-15 (it had pointed at the geoscale5 commit), now one generation later.

## What Happened / Decided

- **AW-292** created: `[Deploy]` story under AW-222, assigned Anagh, Backlog, same label set as AW-285 (`deployment`, `group-mlops` on top of the standard family). Gated on the production run — Courtney runs the committed notebook and posts the run record on the ticket before anything lands.
- **AW-285** received a STOP comment (superseded; do not drop the 2026-07-15 package; remaining acceptance criteria transfer to AW-292). Transition to Done-as-superseded pending — the board has no Cancelled state.
- The discriminating-reads check went into AW-292's serving verification (social ≈ $2.75 / display ≈ $2.78 train-window vs ≈ $5+ under the rejected spec) because `model_version` alone cannot distinguish the two artifact sets.

## Rationale

- A fresh story rather than a second AW-285 rewrite: AW-285's body is dominated by the 2026-07-15 run record of the rejected spec — a rewrite would destroy the historical record of what was almost shipped, and its comment thread already reflects the AtoSscale3 timeline. Supersession keeps both records honest.
- The full-replacement requirement is the load-bearing instruction: because the rejected artifact reached the live API stamped with the same `model_version` the replacement will carry, a merge or partial copy produces a mixed artifact set that no downstream check can detect.

## Follow-ups

- Courtney: run the v2026_5 production notebook end-to-end; post run record + artifact inventory on AW-292.
- AW-285 → Done as superseded once acknowledged.
- AW-286 remains open (root cause unconfirmed) — unchanged by this supersession.
