---
date: 2026-07-27
author: Courtney <jperigo@gmail.com>
type: planning
scope: [board]
summary: The async scenario planner was planned and delivered in the same day — AW-310 and AW-311 both closed, nine stories, across API and GUI. Records the two things a future agent should not have to re-derive: that AW-315's "two runners" was corrected to one on measurement (and why that decision will not move without AW-321), and that four separate claims recorded on the board during delivery had to be corrected by later measurements, which is worth knowing when reading those comment threads.
issues: [AW-310, AW-311, AW-312, AW-313, AW-314, AW-315, AW-316, AW-317, AW-318, AW-319, AW-320, AW-321, AW-248, AW-249]
---

# Async Scenario Planner: Planned and Delivered Same Day

## Context

The [morning planning pass](2026-07-27-async-scenario-planner-planning-jperigo.md) created AW-310 and AW-311 with nine stories, as the first work under the InsightCore v2 initiatives. All nine closed the same day, plus one new spike. This entry records what changed between the plan and the delivery, since several board items now carry corrections that a reader will hit before the conclusion.

## What Happened / Decided

- **AW-310** (under AW-248) and **AW-311** (under AW-249) both **Done**, with all nine stories. The synchronous scenario endpoint returns 501; scenario runs are asynchronous jobs scoped by capability token.
- **AW-321** created — `[Spike]` on scenario scoring cost, under AW-310.
- **AW-315 changed materially during delivery.** Its body specifies two runner instances. That was sized from the 2026-07-22 OOM record's `anon-rss` (~10.4 GB). A measured run peaked at **≥18 GiB**, warm as well as cold, so **one runner is the ceiling** — two is ≥36 GiB against 31 GB with no swap. The story was closed with the correction in its comment thread rather than by rewriting the body, so the original sizing and the reason it was wrong both survive.
- **AW-311's design target moved twice** — from ~100 s (the figure inherited from the 2026-07-03 incident), to ~976 s, and finally to **~120 s steady state with a ~976 s tail** after each new artifact. Both comments are on the epic.

## Rationale

Two things are worth not re-deriving:

**Why the runner count will not move on request.** It is not conservatism and it is not about artifact size. A single Whataburger scenario allocates ≥18 GiB *transiently, during scoring* — measured on a warm run, so it is not compilation overhead that warmth removes — and the figure is clamped by `MemoryHigh`, making it a floor rather than a measurement of demand. Two of those exceed the host even if nothing else runs on it. Retiring the synchronous endpoint (AW-316) freed API memory but does not change this. The only route to a second runner is **AW-321** reducing the peak, with geo-chunking as the lead because batching and concatenating cuts memory without touching the statistics.

**Why several board comments contradict each other, in order.** Four claims recorded during delivery were corrected by later measurements: an OOM diagnosis retracted and then reinstated on deploy-log evidence; the 10.4 GB sizing; a verdict that the MMM cache "optimises a rounding error"; and an apparent 10× scoring regression against 2026-07-03 that turned out to be a cold run compared against a warm one. Each correction is a comment rather than an edit, so the threads read as a sequence. That is deliberate — a reader who sees only the conclusion loses the reason the earlier number looked convincing, and the specific trap (reading `anon-rss` off a process the kernel had just killed, as though it were a capacity requirement) is the kind that recurs.

## Follow-ups

- **Not on the board yet, and should be:** dropping the API service's `MemoryHigh`/`MemoryMax` from 20G/24G to ~3G/4G. Until that lands the containment is nominal — request workers have no code path to load an artifact, but still have the budget to hold one.
- `warm_active_clients` remains reachable behind a default-off env var, so AW-316's "unreachable from any API worker" holds for the request path but not absolutely.
- AW-321 is unassigned and unscheduled.
- Three standing items outside this epic: the advisories pipeline shipped across three repos but is still recorded as deferred; the JDS saturation sidecar fails on a missing artifact coordinate; and twelve smoke tests have been red long enough that two genuinely broken tests hid inside them for 83 days.
