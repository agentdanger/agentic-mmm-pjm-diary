---
date: 2026-07-09
author: Courtney Perigo <jperigo@gmail.com>
type: convention-change
scope: [conventions]
summary: Extended the no-diary-references hard rule from the Jira board to ALL Atlassian products — with Confluence now connected (read/write via the Rovo integration; the DSKB Data Science Knowledge Base space is live), no Atlassian content anywhere may reference the agentic diaries.
issues: []
---

# Convention Change — No Diary References Anywhere in Atlassian

## Context

Confluence became reachable through the same Rovo/Atlassian integration that serves the Jira board (owner re-authorized the connector with Confluence scopes, 2026-07-09). The site already carries a **Data Science Knowledge Base** space (`DSKB`, created 2026-07-03 — the concrete outcome of the AW-238 knowledge-base epic) plus personal spaces. The existing hard rule against referencing the agentic diaries was written board-only; with agents now able to write Confluence pages, the boundary needed an explicit ruling before any page got authored.

## What Happened / Decided

Owner's ruling, verbatim intent: **"we should never reference agentic diaries in any Atlassian entry across their products."** The hard rule is now Atlassian-wide — Jira issues (descriptions, ACs, comments, titles) and Confluence (pages, comments, attachments), extending automatically to any Atlassian product adopted later. Amended [conventions.md](../conventions.md), [CLAUDE.md](../CLAUDE.md), and the [INDEX](../INDEX.md) statements of the rule. Permitted references are unchanged: real artifacts (notebooks, commit SHAs, datasets), Jira keys, and Confluence pages. Diaries may still cross-reference each other internally.

## Rationale

The original rule exists because Atlassian content is team- and client-visible and must stand on its own; the diaries are an agent-facing working layer. That reasoning is about the *audience*, not the *product* — so it applies with equal force to Confluence, and pre-deciding it prevents the first knowledge-base page from setting a bad precedent. One-way visibility is preserved: diaries may link to Jira keys and Confluence pages (they do), Atlassian content never links back.

## Follow-ups

- Apply the rule when drafting any DSKB knowledge-base page (AW-238/AW-240/AW-241 deliverables are the likely first writes).
- Strip any diary reference found in existing Confluence content, same as on the board (none known today — the spaces are days old).
