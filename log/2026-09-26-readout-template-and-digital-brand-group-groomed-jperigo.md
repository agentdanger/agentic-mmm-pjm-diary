---
date: 2026-09-26
author: Courtney <jperigo@gmail.com>
type: grooming
scope: [board]
summary: Closed out two days of JD Sports work onto the board at session end. Three stories under AW-370 for the quarterly readout template, the digital-brand arm and its adoption; one Bug under AW-348 for the MCP's silent saturation-geo fallback; an interim-state comment on AW-410. AW-432 (the adoption) was created Done by reflex and moved back to In Progress because two of its acceptance criteria wait on the host sync and Monday's promotion.
issues: [AW-370, AW-348, AW-410, AW-430, AW-431, AW-432, AW-433]
---

# Readout Template and Digital Brand Group Groomed at Session Close

## Context

The 2026-09-24 board refresh left AW-370 (the v2026_7 model line) as the open
container for JD Sports model work. Two days of work followed with nothing on
the board: the client readout became a template driven by the MCP, and the
team's request to report Google Brand and Meta Brand as digital brand became
a modelling change, tested as an arm, adopted, pushed to the schedule and
published to the host. The owner asked for the session to be closed out with
the diaries, the board and every repo brought current.

## What Happened / Decided

**Under AW-370, three stories.**

| Key | Type | Status | Outcome recorded |
| --- | --- | --- | --- |
| AW-430 | `[Build]` Quarterly readout template fed by the InsightCore MCP | Done | mmm-eom-jdsports `b85f43c`, `60c75ef`, `12691a2`, `f6e9b24`; Q2 FY2027 draft built |
| AW-431 | `[Spike]` Google Brand and Meta Brand as their own group | Done, go | mmm-jdsports `c830d53`, `4b55ea5`; fit unchanged on the candidate's window |
| AW-432 | `[Build]` Adopt the digital_brand group and ship it | In Progress | mmm-jdsports `d2c87be`, mmm-eom-jdsports `0d681b2`; schedule recreated; blob-only fit `…c697d346` uploaded |

**Under AW-348, one Bug.** AW-433: `get_saturation` returns the national
payload when a tier id carries a space, because the API keys geos by the
saturation file suffix and the MCP strips the fallback note. Parked under
the open API epic beside AW-428 and AW-429, since the MCP still has no
container of its own.

**AW-410 commented.** The interim blob-only fit is served once the host
syncs but is not on the OneLake record; the story still covers promoting
Monday's scheduled fit through the pointer row, and the mask rebuild is due
after the interim sync.

**AW-432 corrected from Done to In Progress.** It was created straight into
Done with the other two because the code work is finished, but two of its
acceptance criteria are not: the host-side verification after the sync, and
Monday's promotion. Definition of Done says every criterion checked, so it
went back to In Progress the same minute.

## Rationale

**The readout template is model-line work, not platform work.** It reads the
served model through the MCP and reproduces the GUI's arithmetic, but it is a
client deliverable for JD Sports, and the deliverable-shaped stories on this
line (AW-384, the disclosure) already sit under AW-370. A platform story under
AW-248 would have implied an API change that did not happen.

**One spike and one build for the brand group, not one story.** The arm was
a go/no-go with a measurable verdict; the adoption is deployment work with a
different definition of done and an open tail on the host. Recording them
separately keeps the verdict readable on its own and leaves the open work
visible on the board rather than buried under a closed spike.

**The bug belongs to the serving layer, whichever repo fixes it.** The API
could normalise the id or the MCP could surface the fallback; the trackable
outcome is the same either way, so it sits under the API epic with the other
MCP defect and names both fixes in its acceptance criteria.

## Follow-ups

- AW-432 closes on the host verification and Monday's promotion (AW-410).
- AW-400, the first unattended scheduled run, is Monday 2026-09-28; it now
  runs the digital-brand code, since the schedule was recreated on 2026-09-25.
- An InsightCoreMCP epic or initiative is still owed; AW-427, AW-429 and
  AW-433 are parked under AW-348 and AW-374 meanwhile.
- Assignees remain unset on every item created since 2026-09-24.
