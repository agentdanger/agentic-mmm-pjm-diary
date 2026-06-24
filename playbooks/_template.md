# Playbook: _template

> Meta-template for a new playbook. Playbooks are repeatable project-management procedures (cadence, grooming, item creation). One procedure per file.

Use this shape:

1. **One-line `>` blockquote** — what the procedure is, in a sentence.
2. **When to use** — the trigger, and what should *not* trigger it.
3. **Prerequisites** — board pulls (JQL) and reference files needed first.
4. **Steps** — explicit, ordered; name the JQL/MCP tool calls where relevant.
5. **Verification** — concrete checks that it worked.
6. **Output** — whether it produces a `log/` entry, and when.
7. **Troubleshooting** — common failure modes and fixes; grow this over time.

Keep playbooks grounded in how the team actually works on AW. If a procedure only ever runs once, it's a `log/` entry, not a playbook.
