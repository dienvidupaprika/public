# CLAUDE.md

## Project Context

Read ALL .md files in this project before taking any action:
- masterplan.md — what we're building and why
- design.md — visual design, colors, typography
- implementation.md — technical architecture, file structure
- rules.md — constraints and behavior rules (READ THIS CAREFULLY)
- tasks.md — ordered task checklist

## Workflow

1. Read tasks.md
2. Find the next incomplete task (marked with `[ ]`)
3. Execute ONLY that task
4. Report what you did, what files changed, and what to test
5. Wait for confirmation before proceeding

## Rules

- Do NOT combine multiple tasks into one action
- Do NOT add features, styles, or code not specified in the planning docs
- Do NOT modify files outside the project folder
- Do NOT skip verification steps
- If something seems missing from the spec, ASK — don't guess
- After completing a task, tell me exactly how to verify it worked

## When Debugging

- Reference the specific file and function name when reporting issues
- Check rules.md "Lessons Learned" section for known gotchas
- If you fixed a non-obvious bug, suggest a new entry for rules.md "Lessons Learned"
