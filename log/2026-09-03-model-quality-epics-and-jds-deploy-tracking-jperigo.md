---
date: 2026-09-03
author: Courtney Perigo <jperigo@gmail.com>
type: decision
scope: [board, conventions]
summary: Both client lines had model-quality work landing in containers that don't own it, because AW-215 and AW-217 closed and nothing replaced them. Created AW-344 (JDS) and AW-347 (WAB) as bounded model-quality epics and homed the control-prior work under each. Also ruled that the JDS v2026_6 artifact deploy gets no work item at all — the tactic breakout is its carry to production.
issues: [AW-344, AW-345, AW-346, AW-347, AW-309, AW-253, AW-227, AW-215, AW-217, AW-340, AW-341]
---

# Model-Quality Epics for Both Clients, and a Deploy That Deliberately Isn't Tracked

## Context

A board walk across both client lines, prompted by the control-prior Ridge defect needing a
home. The defect is confirmed on WAB and unaudited on JDS, and neither client had an open
epic that owns model-quality work.

## What Happened / Decided

**The JDS v2026_6 artifact deploy will not be tracked by any work item.** AW-309 is Done and
unassigned while the API still serves v2026_5. Rather than reopen it or create a successor,
the owner ruled that **the channel-tactic breakout is the first carry of v2026_6 to
production** — the artifact ships when that model version ships, so a standalone deploy story
would track a step that no longer exists on its own.

**Two new epics, one per client, both under AW-153 and both Backlog:**

| Key | Epic | Holds |
| --- | --- | --- |
| AW-344 | JDS MMM: Model Quality Enhancements (v2026_6 line) | AW-345 `[Spike]` — audit the JDS control-prior derivation |
| AW-347 | WAB MMM: Model Quality Enhancements (v2026_6 line) | AW-346 `[Build]` — replace the Ridge-derived control-prior means |

AW-346 was created under AW-227 first and re-parented to AW-347 once the epic existed.

**The defect and its asymmetry.** The control-prior Ridge runs `fit_intercept=False` against
uncentered controls, so the fit recruits them as level proxies and the derived means are not
partial effects. On WAB this is measured and a replacement is built, so it is a `[Build]`.
On JDS the same derivation recipe has never been checked, so it is a `[Spike]` ending in a
go/no-go — writing it as a build would assert a defect nobody has confirmed.

**A contradiction found and left standing.** AW-340 and AW-341 both state that v2026_6 ships
the AW-294 weather fix only and that the derivation is unchanged. That does not match the
supersession decision recorded on 2026-08-26. It is written into AW-347's risks section
rather than resolved unilaterally, because it is a scope ruling, not a board-hygiene fix.

## Rationale

**Both clients hit the same failure, from opposite directions, and it is the pattern named on
2026-09-02.** AW-215 and AW-217 — the two Model Quality Refinement epics — are Done. Work
that belongs to them keeps arriving, because a model line does not stop having quality
questions when a refinement epic closes. On JDS that work had nowhere to go and simply went
untracked. On WAB it went somewhere wrong: AW-227, scoped to *model inputs and enrichment*,
had accumulated a version port, an artifact deploy and a prior-derivation build. Silent
absence and quiet scope drift are the same defect, and neither is visible from a board walk
that only asks whether items have parents.

**So the rule generalises: a closed epic on a live model line is a standing liability, not a
finished piece of history.** When an epic closes on a line still in production, either the
next container exists or the next piece of work lands in the wrong one. Creating the
successor at close time is cheaper than discovering the drift a version later.

**The epics are bounded on purpose.** "Additional enhancements" was the request; a
catch-all was the risk. Each is scoped to *the current version line*, excludes the
neighbouring epics by key, and carries success criteria that can actually be met — for JDS,
that the derivation is confirmed sound or repaired before v2026_6 is carried to production.
An epic that can never be Done is the failure mode AW-243 was reframed to avoid.

**Not tracking the JDS deploy is a real decision, not an omission.** A Done tick on a board
with no Cancelled state is ambiguous by construction, so it is worth stating plainly: AW-309
is closed and nothing replaces it, because the deploy is no longer a separable step. The
risk this accepts is that v2026_6 stays unserved for as long as the breakout takes, and that
the JDS derivation audit therefore has to land before that carry rather than before a deploy
of its own. AW-344's success criteria say so.

## Follow-ups

- Rule on the AW-340 / AW-341 scope contradiction — whether v2026_6 ships the weather fix
  alone or bundles the derivation replacement. AW-346 cannot be sequenced until it lands.
- Re-parent AW-290; it sits under AW-217, which is Done, so it is invisible in hierarchy
  views. It may also want splitting, since it spans a producer artifact change and a GUI
  change.
- Add the vintage-identifier question to AW-288: whether feed drops can publish an identifier
  so a restatement is detectable at read time rather than after a comparison consumes it.
- No board item covers the flagged snow magnitudes held for review before client use, on
  either client.
