# Template: _template (how to write a template)

> Meta-template. Use this shape when adding a new item-type template to this folder. Templates exist so agents can produce board-ready drafts without re-deriving structure each time.

Each item-type template should contain, in order:

1. **A one-line `>` blockquote** — when to use it, whether it links to a parent, and a reference to a real example item on the board.
2. **A metadata line** — `Type · Parent · Labels · Status on create`.
3. **Summary (title)** — the title pattern, including the prefix taxonomy if it's a Story variant.
4. **Description** — the exact body skeleton, in a fenced block so it's copy-pasteable, using clean Markdown headings and `- [ ]` checkboxes. **The skeleton must not itself wrap the description in a ` ```markdown ` fence** — that renders as a code block in Jira.
5. **A "Checklist before creating"** — the subset of the [trackability checklist](../conventions.md) that matters for this type.

Keep templates grounded in real items — cite the board keys they're modeled on so the convention stays anchored to practice. When the team's practice shifts, update the template and note it in `log/`.
