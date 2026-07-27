---
date: 2026-07-27
author: Courtney <jperigo@gmail.com>
type: planning
scope: [board]
summary: Planned the asynchronous scenario planner across both InsightCore initiatives — AW-310 (Epic under AW-248, API) and AW-311 (Epic under AW-249, GUI), with nine stories. First work planned under either initiative since they were created empty on 2026-06-24, closing that pass's open follow-up. Records the three owner decisions that are easy to re-litigate later and expensive to get wrong: the job store is the filesystem rather than any database, the sync endpoint returns 501 rather than being deprecated-but-live, and two runners is a measured ceiling rather than a starting guess. Also records the cross-initiative gate — AW-316 must not land before AW-311 is live in production.
issues: [AW-310, AW-311, AW-312, AW-313, AW-314, AW-315, AW-316, AW-317, AW-318, AW-319, AW-320, AW-248, AW-249]
---

# Async Scenario Planner: Planning Across AW-248 and AW-249

## Context

A capacity review of the shared API/GUI/MCP host on 2026-07-27 found that the scenario planner is the only workload constraining the box, that it runs with no admission control of any kind, and that an undetected OOM outage on 2026-07-22 had already been caused by it. The structural fix — making scenario runs asynchronous with a bounded runner pool — needed planning onto the board. It spans both reporting-layer initiatives, since the API and the GUI each change.

AW-248 (*InsightCore API v2*) and AW-249 (*InsightCore GUI v2*) were created on 2026-06-24 deliberately empty, with "convert candidate pillars into epics" as the stated follow-up. Both were still childless. This is the first work planned under either, and AW-310 lands directly in a pillar AW-248 already names — *scenario planning & performance*.

## What Happened / Decided

- **AW-310** created as an Epic under **AW-248** — asynchronous scenario execution — with six stories: **AW-312** (filesystem job store, atomic claim), **AW-313** (submit/status/result endpoints), **AW-314** (runner service), **AW-315** (`[Deploy]` host provisioning: data root, runner units, memory-capped slice), **AW-316** (retire the synchronous endpoint), **AW-317** (retention sweep and stale-runner recovery).
- **AW-311** created as an Epic under **AW-249** — the submit-and-poll experience — with three stories: **AW-318** (persist job tokens, My Runs list), **AW-319** (poll and render), **AW-320** (recover a run by token).
- All eleven land in Backlog, unassigned, Medium priority. Labels follow the June convention for these initiatives: `DataScience`, `InsightCore`, `client-shared`, `group-data-science`, `group-platform`, plus `api` or `gui`. **`Modeling` is deliberately omitted** — reporting-layer work, matching how AW-248/249 were labelled. AW-315 additionally carries `group-mlops`, `deployment`, `infrastructure`, being the only host-side story.
- Engineering-side design is recorded in the InsightCore diary as two architecture entries — the ownership model (capability tokens, no accounts) and the build plan (job store and runner) — with the outage itself written up as a 2026-07-22 incident. Board content deliberately carries none of those references, per the Atlassian rule; the issue bodies cite commits `ec84b4e` and `1c85a2e` and repo paths instead.

## Rationale

Three decisions are recorded here because they will look arbitrary later and are expensive to reverse:

- **Filesystem, not a database.** The instinct on hearing "job queue" is to reach for Postgres, Redis, or a document store. The deciding argument is not preference: scenario results are multi-megabyte blobs that belong on disk regardless, so *any* database would be a second storage system rather than a replacement for the first, and the atomic claim that usually forces a database is free from POSIX `rename()`. SQLite is the designated upgrade path. A graph database was considered and rejected outright — the model has no edges and one access pattern. **The trigger that reverses this is topology, not data model:** a second host makes a filesystem store unworkable, which is why the store sits behind a narrow interface.
- **The sync endpoint returns 501, not a deprecation notice.** Keeping it serving "just in case" was the tempting option. It is also the unbounded memory path — the one that lets an arbitrary number of workers each load a ~10.4 GB artifact — so leaving it alive would preserve the exact exposure the work exists to remove and make the runner's concurrency cap cosmetic. There must be exactly one way to run a scenario.
- **Two runners is measured, not conservative.** A Whataburger run holds ~10.4 GB resident against 31 GB with no swap; two runners plus the API baseline is ~22 GB, three is ~32 GB and past the physical limit. The number is written into AW-315's body *with* the arithmetic specifically so a future reader does not raise it as an easy optimisation.

Two further points of reasoning worth not re-deriving:

- **No job-list endpoint, ever.** Ownership without a login works because possession of an unguessable token is the only permission. A single endpoint that lists or searches jobs collapses that in one commit, and it is exactly what someone adds while debugging. It is therefore an acceptance criterion with a test on AW-313, not a design note.
- **Why an Epic under each initiative rather than one epic spanning both.** An epic has one parent, and this work genuinely delivers two separable outcomes: a job API that stands on its own, and a GUI experience that consumes it. Splitting keeps each initiative's scope honest and makes the dependency explicit rather than implicit.

## Follow-ups

- **AW-316 must not be started before AW-311 is live in production.** The gate is stated in both epics' bodies; it is the one ordering error in this plan that would break the planner for users.
- AW-315 and AW-317 include systemd work that cannot be delivered by a code push — the API deploy script does not copy unit files, so units and drop-ins are maintained on the host directly. Whoever picks these up needs box access.
- Assign owners before anything moves to Selected for Development; all eleven are currently unassigned.
- AW-248 and AW-249 still lack a bounded definition of done. This pass added their first epics but did not close the June follow-up in full — enumerating the remaining epic set for each initiative is still outstanding.
