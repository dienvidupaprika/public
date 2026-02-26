# Plan-First Vibe Coding

A practical toolkit for building real software with AI agents. Five planning templates, a rules file, and guides for non-developers.

Works with Claude Code, Cursor, Lovable, or any AI coding tool.

## Background

Lazar Jovanovic (Lovable's first professional vibe coder) laid out the philosophy on [Lenny's Podcast](https://www.lennysnewsletter.com/p/the-rise-of-the-professional-vibe): spend 80% of your time planning, 20% executing. Use PRDs as persistent context. Feed the agent one task at a time. Read the agent output instead of the code.

The approach resonated with me. I applied it to a personal project, and by the time the planning docs were done, the build phase was just "proceed with the next task" and verify. This repo packages that system into reusable templates so you can do the same.

## Quick Start

1. Download this repo (Code → Download ZIP)
2. Create a folder for your project and copy `CLAUDE.md` into it
3. Open the folder in your AI tool (see [`guides/TOOL-SETUP.md`](guides/TOOL-SETUP.md) for setup)
4. Say **start**

The agent walks you through a structured planning conversation, asking the right questions at the right moments. By the end, you have five spec docs in your project folder. Then say **build** and the agent executes one task at a time while you verify.

| Command | What it does |
|---|---|
| **start** | Begin the planning exercise |
| **build** | Start the build phase (after planning is done) |
| **resume** | Pick up where you left off in a new session |
| **status** | See what's done and what's next |

## What's Here

### The Agent ([CLAUDE.md](CLAUDE.md))

Drop this into your project folder. It drives the entire workflow: planning conversation, spec creation, build execution, and debugging. This is the only file you need to get started.

### Templates (reference structures)

The agent uses these as scaffolding when building your spec docs. You don't fill them in manually — the agent creates them through conversation with you. But you can read them to understand what good planning looks like.

| File | What it becomes |
|---|---|
| [masterplan.md](templates/masterplan.md) | What you're building and why |
| [design.md](templates/design.md) | How it looks and feels |
| [implementation.md](templates/implementation.md) | How it's built technically |
| [rules.md](templates/rules.md) | Agent behavior constraints |
| [tasks.md](templates/tasks.md) | Ordered build checklist |

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

The agent asks the questions that prevent bugs before they happen:

- Does your project involve calculations? It won't move on until you've defined a reference test case with known correct values.
- Will it display numbers? It asks for the exact format per locale, because the agent defaults to US formatting otherwise.
- It checks task dependencies: if Task 7 would call functions from Tasks 8 and 9, it structures the tasks so nothing breaks mid-build.
- It asks what happens when the user enters 0, clears the field, or types letters.

These questions came from real builds. Each one represents a bug that was either caught during planning or learned the hard way during execution.

## Who This Is For

- Non-developers building with AI tools who want structure, not chaos
- Developers who want a planning system that works across tools
- Anyone who's tried vibe coding and produced something that kind of works but is fragile

## FAQ

**How long does the planning phase take?**
About 1-2 hours of conversation. The agent asks the questions; you just answer. Feels like a lot until you realize you'd spend that time anyway on re-prompting, debugging, and explaining context the agent has already forgotten.

**Do I need to know how to code?**
No. The agent guides the planning through conversation, builds the code for you, and tells you exactly what to test after each step. The [Testing Guide](guides/TESTING-GUIDE.md) covers everything from opening a browser console to deploying on Netlify.

**Can I use this with [tool]?**
If your tool reads markdown files and writes code, yes. Tested with Claude Code, but `CLAUDE.md` works with Cursor, Lovable, Windsurf, or any AI coding agent. For Cursor, rename it to `.cursorrules`.

**What if my project doesn't involve calculations or multiple languages?**
The agent only asks questions that are relevant. If your project doesn't have formulas or locale requirements, it skips those sections.

**Is this overkill for a simple project?**
If you're building a throwaway prototype, just vibe. If you're building something that needs to be correct, maintainable, or used by other people, the planning pays for itself.

## Credits

The philosophy comes from Lazar Jovanovic. Watch his full interview on [Lenny's Podcast](https://www.lennysnewsletter.com/p/the-rise-of-the-professional-vibe).

The templates and guides are by [Madara Knutina](https://www.linkedin.com/in/madaraknutina).
