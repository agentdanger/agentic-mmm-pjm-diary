---
date: 2026-09-24
author: Courtney <jperigo@gmail.com>
type: grooming
scope: [board, conventions]
summary: The JD Sports board had not moved since 2026-09-09 while the tactic breakout shipped, the control-prior audit was answered, the gold layer was built, v2026_7 went live and became a scheduled Azure ML job publishing to OneLake. Closed five existing items on their outcomes, commented three others, created five epics and fifty-five stories (twenty-seven Done with commits), populated the two empty infrastructure epics AW-245 and AW-247, and stood up the API and GUI re-architecture epics plus a JDS migration epic, all three explicitly planned-not-finalized and gated on an architecture spike.
issues: [AW-253, AW-281, AW-343, AW-344, AW-345, AW-221, AW-289, AW-256, AW-245, AW-247, AW-348, AW-370, AW-371, AW-372, AW-373, AW-374]
---

# JD Sports Board Refresh: v2026_7, Gold, OneLake, and the Serving Re-architecture

## Context

The owner asked for the JD Sports board to catch up with two weeks of model and infrastructure change and to capture the planned re-architecture of the reporting layer onto Azure reading OneLake. A board walk found the last JD Sports update on 2026-09-09, AW-343 In Progress for work that had shipped, AW-281 and AW-345 in Backlog with their verdicts already known, and the two infrastructure epics that own the job path and the artifact handoff (AW-245, AW-247) with zero stories.

## What Happened / Decided

**Five existing items closed on their outcomes, each with a comment recording the deviation.** AW-343 Done: the breakout columns landed in the gold layer rather than a dev dataset, because the AW-256 dev/prod split does not exist for JD Sports. AW-281 Done, go: the verdict came from a full v2026_7 fit rather than a dev-dataset capacity test, with per-tactic grades from the evidence method. AW-253 Done on that verdict; no separate implementation epic, since the implementation was the model line. AW-345 Done, go: the Ridge defect was present and repaired in v2026_7. AW-344 Done as superseded: v2026_6 never served.

**Three comments without status change on other people's items.** AW-221 (Billy) got the three gold-build findings that bear on the revenue discrepancy. AW-289 (Victoria) got what the gold gate now enforces so the SLA can reference it. AW-256 (Anagh) got the note that gold is currently both dev and prod for JD Sports.

**Five new epics.**

| Key | Parent | Holds | Status |
| --- | --- | --- | --- |
| AW-370 | AW-153 | JDS MMM v2026_7: the model line on gold. 9 Done, 3 Backlog | In Progress |
| AW-371 | AW-153 | JDS gold training table in Fabric. 8 Done, 1 Backlog | In Progress |
| AW-372 | AW-248 | InsightCore API v3: Azure container app reading OneLake. 7 Backlog | Backlog |
| AW-373 | AW-249 | InsightCore GUI v3 on Azure. 5 Backlog | Backlog |
| AW-374 | AW-153 | JDS migration to the OneLake-backed serving architecture. 4 Backlog | Backlog |

**The two empty infrastructure epics were populated rather than duplicated.** AW-245 (automated refresh) took the environment, job, schedule and vintage guard as Done plus four Backlog items (first unattended run, shared GPU cluster, CSV retirement, key rotation). AW-247 (artifact handoff) took Files, tables, registry, promotion tool, sidecars and the generated production notebook as Done plus the first promotion and the probe-table drop; it moved from Backlog to In Progress. This keeps AW-243 at its eight epics.

**Two immediate defects filed under AW-348** as Bug stories, since it is the open API-side container: the stale-mask loader (AW-428) and the MCP fiscal calendar (AW-429). The MCP has no epic of its own; the second bug says so.

**Three labels coined:** `fabric`, `onelake`, `azure-ml`. None existed on the board.

**Full bodies** are in `jira-drafts-2026-09-24.md` at the workspace root, with every commit and artifact cited. No Atlassian item references a diary.

## Rationale

**The gold layer went under AW-153, not AW-243.** It is client-specific data engineering for one model line. AW-243 was reframed on 2026-06-29 as bounded to its capability epics, and adding a ninth would reopen that boundary. The epic body says so and invites a re-parent if the team disagrees.

**Job, registry and lakehouse publish went into AW-245 and AW-247 rather than a new epic.** They are exactly the capabilities those epics were created to hold, and both had sat empty since July. Populating them with the JD Sports instance (labelled `client-jdsports`) makes the infrastructure initiative reflect what has actually been built.

**The re-architecture is three epics, each led by a spike with a go/no-go.** The owner said the design is planned and not finalized. Writing build stories without that gate would assert decisions nobody has made (hosting, identity to OneLake, where the 19 GB runner lives). Each epic's goal states the planned-not-finalized status in bold, and the JDS migration epic (AW-374) says nothing in it starts until the API spike lands. Per the AW-248/AW-249 rule, API and GUI got separate epics; the client migration sits under the model initiative because it is JD Sports serving work, not platform work.

**Done stories were created straight into Done with their commits.** Same precedent as 2026-09-11: the board is a record, and a story whose acceptance criteria are already met and whose commit is known should not sit in Backlog to be groomed.

**AW-344 closed as superseded rather than left open.** A closed epic on a live model line is the standing liability named on 2026-09-03, but here the successor (AW-370) exists and holds the quality work, so closing is safe. Leaving it open would suggest v2026_6 might still ship.

## Follow-ups

- Assign owners: AW-395 (catalogue feed) is data engineering's; AW-400 (first unattended run) and AW-410 (first promotion) are the owner's for Monday 2026-09-28; AW-412 (API architecture spike) decides whether the other 15 re-architecture stories proceed.
- An InsightCoreMCP epic or initiative, so AW-429 and AW-427 have a proper home.
- Re-parent AW-371 under AW-243 or AW-256 if the team prefers the gold layer counted as infrastructure.
- `conventions.md` still describes AW-243 as "seven capability epics"; it has been eight since June. Stale, unrelated to this change.
