---
date: 2026-06-29
author: Courtney Perigo <jperigo@gmail.com>
type: decision
scope: [board, modeling-direction]
summary: Set the WAB new-market-fit direction — solve it in the unified single model via the intercept fix (activation-gated baseline), not a separate model that borrows national media. Closed AW-223 (characterization done) and AW-224 (w_g treatment shipped), opened AW-260 for the intercept-fix build (exposure-controls exploration folded in), and moved AW-260 + AW-225 to In Progress.
issues: [AW-222, AW-223, AW-224, AW-225, AW-260]
---

# WAB New-Market Fit — Direction Set to the Intercept Fix (Single Model)

## Context

WAB new-market fit (AW-222) had three Backlog stories that no longer matched where the modeling work had actually gone. A board review against the live R&D showed the epic implied options the team is no longer pursuing, and that the current breakthrough wasn't tracked at all. The owner set the direction and the board was reconciled to it.

## What Happened / Decided

The chosen approach for new-market fit is the **intercept fix in the unified single model** — an activation-gated baseline — explicitly **not** a separate expansion model that borrows media from the national model. Board changes under AW-222:

- **AW-223** (`[Spike]` characterize thin-data markets + store↔media confound) → **Done.** Closing comment records the operational market definition (recent new-store share ≥ 0.25 AND v2026_3 holdout MAPE > 10% → 9 expansion / 48 core), the unit + DMA confound quantification, opening dynamics, and the zero-padding root cause.
- **AW-224** (`[Build]` dynamic self-retiring data-limited treatment) → **Done, closed as already shipped.** Its acceptance criteria describe the `w_g` / `geo_data_weight` shrinkage + data-limited flag already live in v2026_3 — a different mechanism from the intercept fix.
- **AW-260** (`[Build]` activation-gated baseline (intercept fix)) → **created under AW-222, In Progress.** Implements an uncentered per-geo `active_gate` that carries born-mid-window markets' post-activation level, with the intercept primed ~0 and born-market detection by global-window activation lateness. The maturity-weighted footprint **exposure** controls exploration is folded into this story as an acceptance criterion (kept here, not split into a separate epic).
- **AW-225** (`[QA]` track expansion-market fit) → **In Progress**, with the live scorecard metric set recorded in a comment.
- **AW-222** carries a "chosen approach" direction comment.

## Rationale

- **The blocker was the intercept, not the feature shape.** R&D showed born-mid-window markets are zero-padded for 50–80% of the window, and a single constant per-geo intercept (`dims=("geo",)`, no time axis) can't represent a 0→activation step, so the activation-period level leaks to media. The fix gives that level an explicit home; in the prototype, born-market media collapses (Charlotte 101→38%, Greenville 121→26%) and born holdout MAPE drops from the 99–160% range to 7–22% (median 16%) with the core untouched (confident-gate 2.17%, national holdout 1.09%). That is why a *new* `[Build]` story was warranted rather than reusing AW-224.
- **AW-224 was shipped work, not the current solution.** Its `w_g` shrinkage softly pulls thin markets toward national and flags them; it does not address where the level goes. Marking it Done (with a comment) keeps the board honest and avoids overloading a story whose ACs describe a different mechanism.
- **Single model, not two.** The owner ruled out the earlier two-model option (a separate expansion model borrowing national media, backing media out post-fit). Recording this prevents a future agent from re-opening that path. The exposure-controls idea stays a complementary lever *inside* AW-260, consistent with AW-222's "cataloguing individual candidate architectures is out of scope."
- **AW-260 + AW-225 reflect reality.** Both are actively being worked, so they belong In Progress, not Backlog.

## Follow-ups

- AW-260: complete the calibration pass (thin-market gate σ; born-market macro shrinkage toward national) and the exposure-controls keep/drop decision; record where the work lands (notebook / commit SHA) on the issue at Done.
- AW-225: keep scoring each iteration against the v2026_3 baseline and record results so progress stays visible.
