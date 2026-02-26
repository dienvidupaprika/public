# Plan-First Vibe Coding

A practical toolkit for building real software with AI agents. Five planning templates, a rules file, and guides for non-developers.

Works with Claude Code, Cursor, Lovable, or any AI coding tool.

## Background

Lazar Jovanovic (Lovable's first professional vibe coder) laid out the philosophy on [Lenny's Podcast](https://www.lennysnewsletter.com/p/the-rise-of-the-professional-vibe): spend 80% of your time planning, 20% executing. Use PRDs as persistent context. Feed the agent one task at a time. Read the agent output instead of the code.

The approach resonated with me. I applied it to a personal project, and by the time the planning docs were done, the build phase was just "proceed with the next task" and verify. This repo packages that system into reusable templates so you can do the same.

## Quick Start

1. Download this repo (Code → Download ZIP) or click "Use this template"
2. Read [`guides/PLANNING-GUIDE.md`](guides/PLANNING-GUIDE.md) — 10 minutes
3. Fill in the five templates in `templates/` — about 2 hours total
4. Copy completed files + `CLAUDE.md` into your project folder
5. Open your AI tool and say:

> Read all .md files in this project. Confirm you've read them, then execute Task 1 from tasks.md. Only Task 1. Show me the verify steps when done.

6. After each task: verify, then say "Execute Task N from tasks.md. Only Task N."

That's the whole workflow. See [`guides/TOOL-SETUP.md`](guides/TOOL-SETUP.md) for Claude Code, Cursor, and Lovable-specific setup.

## What's Here

### Templates (the spec docs)

| File | Purpose | Time to Fill |
|---|---|---|
| [masterplan.md](templates/masterplan.md) | What you're building and why | 30 min |
| [design.md](templates/design.md) | How it looks and feels | 20 min |
| [implementation.md](templates/implementation.md) | How it's built technically | 40 min |
| [rules.md](templates/rules.md) | Agent behavior constraints | 15 min |
| [tasks.md](templates/tasks.md) | Ordered build checklist | 30 min |

### Guides

| File | Purpose |
|---|---|
| [PLANNING-GUIDE.md](guides/PLANNING-GUIDE.md) | How to fill in the templates (start here) |
| [TESTING-GUIDE.md](guides/TESTING-GUIDE.md) | Browser console, localhost, debugging for non-devs |
| [TOOL-SETUP.md](guides/TOOL-SETUP.md) | Setting up Claude Code, Cursor, or Lovable |

### Drop-in Agent Config

| File | Purpose |
|---|---|
| [CLAUDE.md](CLAUDE.md) | Rules file for Claude Code — drop into your project root |

## What Makes This Different from "Just Use AI"

The templates have `<!-- QUESTION: -->` prompts embedded at decision points. These force you to think about things that cause bugs later:

- Does your project involve calculations? Define a reference test case with known correct values.
- Will it display numbers? Specify the exact format per locale, or the agent defaults to US formatting.
- Does Task 7 call functions from Tasks 8 and 9? Then Task 7 must not include those calls yet.
- What happens when the user enters 0? Or clears the field? Or types letters?

These questions came from real mistakes made during real builds. Each one represents a bug that was either caught during planning or learned the hard way during execution.

## Who This Is For

- Non-developers building with AI tools who want structure, not chaos
- Developers who want a planning system that works across tools
- Anyone who's tried vibe coding and produced something that kind of works but is fragile

## FAQ

**How long does the planning phase take?**
About 2-3 hours for the five templates. Feels like a lot until you realize you'd spend that time anyway on re-prompting, debugging, and explaining context the agent has already forgotten.

**Do I need to know how to code?**
No. The templates and guides are written for non-developers. The [Testing Guide](guides/TESTING-GUIDE.md) covers everything from opening a browser console to deploying on Netlify.

**Can I use this with [tool]?**
If your tool reads markdown files and writes code, yes. Tested with Claude Code, but the templates work with Cursor, Lovable, Windsurf, or any AI coding agent. The `CLAUDE.md` file is Claude Code-specific; for Cursor, rename it to `.cursorrules`.

**What if my project doesn't involve calculations or multiple languages?**
Delete those sections from the templates. The `<!-- QUESTION: -->` prompts tell you which sections to skip if they don't apply.

**Is this overkill for a simple project?**
Depends on the project. If you're building a throwaway prototype, just vibe. If you're building something that needs to be correct, maintainable, or used by other people, the planning pays for itself.

## Credits

The philosophy comes from Lazar Jovanovic. Watch his full interview on [Lenny's Podcast](https://www.lennysnewsletter.com/p/the-rise-of-the-professional-vibe).

The templates and guides are by [REPLACE: your name and link].

## License

MIT — use it, fork it, adapt it, share it.
