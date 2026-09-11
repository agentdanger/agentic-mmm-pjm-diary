---
date: 2026-09-11
author: Courtney <jperigo@gmail.com>
type: grooming
scope: [board]
summary: Groomed the day's InsightCore work into two epics — AW-348 (API, under AW-248) and AW-349 (GUI, under AW-249) — with nine and eight stories; fourteen Done with commits recorded, three API follow-ups in Backlog, one dropped as a duplicate of AW-321. Created and transitioned the same day once the connector was back.
issues: [AW-248, AW-249, AW-348, AW-349, AW-321]
---

# InsightCore Horizon, Lagged Effect and Queue Work Groomed into Two Epics

## Context

A single day produced a coherent body of shipped work across both InsightCore repos — the optimizer's objective horizon, after-window media reporting, a queue admission cap, multi-submit, comparison outcomes, and the fixes from a runner throttling incident — with nothing on the board for any of it. The owner asked for tickets, completed where the work is done, and an epic to hold them.

## What Happened / Decided

Two epics rather than one, per the board rule that work spanning the API and GUI layers gets an epic under each initiative rather than one epic with two parents. Labels per the InsightCore convention: `DataScience`, `group-data-science`, `client-shared`, `InsightCore`, plus `api` or `gui`; no `Modeling`.

**API epic** (parent AW-248): "InsightCore API: optimizer objective horizon, lagged-effect reporting and queue admission". Stories: after-window media on scenario results ([Build], Done, 39e8ab6); `objective_horizon` on optimization requests ([Build], Done, 6a1a474); ten-slot weighted queue cap ([Build], Done, bb30082); scores slowed 13x under memory throttling ([Bug], Done, ec26cc7 plus live slice change); deploy path restored — script copy, sudoers, unit install ([Deploy], Done, box-side); rank-agreement verification on Houston ([QA], Done, finding recorded); solve the optimizer with trailing history ([Build], Backlog); claim chained scores ahead of new submissions ([Build], Backlog); thinned-draw scoring ([Spike], Backlog); self-updating deploy wrappers and deployed commit on /info ([Build], Backlog).

**GUI epic** (parent AW-249): "InsightCore GUI: objective horizon choice, lagged-effect section and comparison outcomes". Stories: "Optimize for" choice and horizon chip ([Build], Done, f19a9ad); lagged-effect section ([Build], Done, f19a9ad, c024d3c, 6ca8a5e); comparison CSV outcome rows ([Build], Done, 9a0a557); attributed and CPT per market in comparison ([Build], Done, 1e07e75, f9be48d); queue another optimization while one scores ([Build], Done, 7d42ee3); scored optimizations read "not yet scored" ([Bug], Done, 11268de, f803f17); structured refusals shown as status codes ([Bug], Done, 1069848); GUI auto-deploy failing since August 11 ([Bug], Done, box-side).

Full bodies, drafted to the templates with acceptance criteria and recorded commits, are held outside the board until creation; no Atlassian item references any diary.

## Rationale

The bug-as-story convention fits the incident work: each defect has a reproduce, expected and actual, and each closed on a commit or a recorded box-side change. The rank-agreement check is a `[QA]` story rather than a spike because it validated a shipped capability and its verdict routes into a named `[Build]` follow-up. The four Backlog stories are the concrete next moves the day's measurements point at, not a roadmap; the largest of them, solving with trailing history, is the one that determines whether the optimizer can beat a vetted plan at all.

## Keys (created 2026-09-11 after the connector reconnected)

- **AW-348** — API epic, In Progress. Done: AW-350 after-window media, AW-351 objective horizon, AW-352 queue cap, AW-353 throttle bug, AW-354 deploy path, AW-355 rank-agreement QA. Backlog: AW-356 trailing history, AW-357 chained scores first, AW-358 deploy wrappers and deployed commit.
- **AW-349** — GUI epic, Done. AW-359 objective choice and chip, AW-360 lagged-effect section, AW-361 comparison CSV, AW-362 market attribution in comparison, AW-363 multi-submit, AW-364 "not yet scored" bug, AW-365 structured refusals bug, AW-366 GUI auto-deploy bug.
- The thinned-draws spike was dropped from the drafts: AW-321 already covers it.

## Follow-ups

- Assign an owner to AW-356 (trailing history) before pulling it into In Progress; it is the one story that decides whether the optimizer can beat a vetted plan.
- AW-348 closes when AW-356, AW-357 and AW-358 are Done.
