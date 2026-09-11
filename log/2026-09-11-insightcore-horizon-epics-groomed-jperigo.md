---
date: 2026-09-11
author: Courtney <jperigo@gmail.com>
type: grooming
scope: [board]
summary: Groomed the day's InsightCore work into two epics — one API (under AW-248), one GUI (under AW-249) — with ten and eight stories respectively, most already Done with commits recorded, four API follow-ups in Backlog. Drafted to the templates; creation is pending the Atlassian connector being re-authorized, so no keys yet.
issues: [AW-248, AW-249]
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

## Follow-ups

- Re-authorize the Atlassian connector; create the two epics and eighteen stories from the drafts, transition the Done ones with their commits, and record the keys here.
- Assign an owner to the trailing-history story before pulling it into In Progress.
