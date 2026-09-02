---
date: 2026-09-02
author: Courtney Perigo <jperigo@gmail.com>
type: convention-change
scope: [conventions, board]
summary: A discovery epic excluded feature engineering outright while its own gating spike required a dev-dataset capacity fit — so AW-253 excluded work it depended on. Ruling: whatever is needed to reach the verdict belongs to the discovery epic, scoped against *production*; the implementation epic is still created only when the go/no-go lands.
issues: [AW-253, AW-281, AW-279, AW-280, AW-259, AW-256]
---

# A Discovery Epic Carries the Work Needed to Reach Its Own Verdict

## Context

AW-253 (*JDS MMM: Additional Channel-Tactic Breakouts — Identification*) reached the point where its gating spike could start. Its three discovery stories are closed — AW-279 (taxonomy inventory), AW-280 (business requirements) and AW-291 (client-confirmed brand/performance parsing) — leaving AW-281, the identifiability go/no-go, unblocked in Backlog.

Two stories are needed to bridge them: a specification reconciling AW-279 × AW-280 into an approved candidate list, and a dev-dataset build deriving those splits so the spike has something to fit. The second one had nowhere to live. AW-253's Scope Out read "feature engineering, model changes, deployment," while AW-281's own acceptance criteria require "at least one dev-dataset capacity-test fit carrying the candidate splits." The epic excluded work its own spike depends on.

## What Happened / Decided

Considered three homes for the dev build and rejected two:

- **A new implementation epic, created now.** Rejected. AW-253's Approach note states the implementation epic is "created when the go/no-go lands," and that a no-go closes the epic "with a documented negative and no implementation epic is created." Standing one up before the verdict pre-commits to building breakouts not yet shown to be identifiable, and inverts the decision the epic exists to make.
- **AW-256 (Development & Production Training Datasets).** Rejected. Its Scope Out excludes "feature engineering of specific columns (per-client model work)" — it owns the dataset-separation *capability*, not the columns. It is also `client-shared` where this work is `client-jdsports`.
- **AW-253, with an amended scope.** Adopted.

AW-253's description amended: the Goal clause now reads "Analysis, requirements, and the development-dataset work needed to reach a go/no-go — not production execution or deployment"; Scope In gains "derive candidate splits into the **development** training dataset as instrumentation for the identifiability spike"; Scope Out now excludes **production** feature engineering. A dated *Scope amendment (2026-09-02)* section records the reasoning on the epic itself.

Generalized into [conventions.md](../conventions.md) as a new subsection under the hierarchy rules, so the next discovery epic is scoped correctly at creation rather than amended mid-flight.

## Rationale

The exclusion was written to mean *don't ship breakouts into the production model*. It was not written with the capacity fit in mind — a throwaway dev build whose only purpose is to answer "can the model carry this at all?" is part of the identification question, not implementation of it. Reading the exclusion literally would have forced the implementation epic into existence early, which is precisely the pre-commitment the discovery/implementation split exists to prevent. The cheaper fix is one word: scope the exclusion against *production*.

The precedent already existed and was not followed only because AW-253 was scoped more tightly than its WAB counterpart. AW-259 derived the video-breakout columns into the dev training dataset under AW-227 — the client epic that owned the breakout — referencing AW-256's dev/prod approach rather than being absorbed by it. AW-227's scope happened to include feature engineering, so no tension surfaced there. AW-253's narrower wording is what exposed the gap.

Worth recording the pattern rather than just the instance: this is the third time in one session that work fell into a gap between a closed or too-narrow container and an unowned next step. AW-309 was closed on a condition ("will deploy upon the next model upgrade") that later came and went without the deploy happening, leaving the JDS v2026_6 promotion untracked; the WAB v2026_6 line had no home because AW-222 and AW-217 both closed. The common failure is a container whose boundary is defined by what it *excludes* rather than by the outcome it owns. Here the gap was visible before it swallowed anything.

## Follow-ups

- Create the two bridge stories under AW-253: a `[Data]` specification (Victoria) reconciling AW-279 × AW-280 into the approved candidate list, and a `[Build]` dev-dataset derivation (Anagh). AW-281 stays blocked until both land.
- AW-280 was closed with no output recorded on the issue, so the business-requirements half must be recovered before reconciliation — the Definition of Done's "where the work landed is recorded" was not met.
- Confirm with Billy whether the AW-291 brand/performance parsing has landed in the media feed. It determines whether the dev build reads an already-parsed feed or applies the mapping rules itself — materially different work.
- [conventions.md](../conventions.md) still describes AW-243 as "seven capability epics"; the 2026-06-29 grooming pass moved it to eight. Stale, unrelated to this change.
