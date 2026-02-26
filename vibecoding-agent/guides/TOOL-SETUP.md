# Tool Setup Guide

How to set up your AI coding tool and feed it your spec. Pick one tool
below based on what you have.

## Option 1: Claude Code (VS Code Extension)

**Requires:** VS Code installed, Claude Pro or Max subscription

### Setup

1. Open VS Code
2. Press `Ctrl+Shift+X` (Extensions panel)
3. Search "Claude Code" → install the official Anthropic extension
4. Click the sparkle icon (✱) in the top-right corner, or press
   `Ctrl+Shift+P` → type "Claude Code" → "Open in New Tab"
5. Sign in with your Anthropic account

### Project Setup

1. Create a folder for your project (e.g., `my-project` on your Desktop)
2. Copy your 5 completed template files into this folder:
   - `masterplan.md`
   - `design.md`
   - `implementation.md`
   - `rules.md`
   - `tasks.md`
3. Copy `CLAUDE.md` from this repo into the same folder
4. In VS Code: File → Open Folder → select `my-project`

### First Prompt

Paste this into Claude Code:

> Read all .md files in this project: CLAUDE.md, masterplan.md, design.md,
> implementation.md, rules.md, and tasks.md. These are the complete spec
> for what we're building. Confirm you've read them, then execute Task 1
> from tasks.md. Only Task 1. Show me the verify steps when done.

### Ongoing Prompts

After verifying each task passes:

> Execute Task 2 from tasks.md. Only Task 2.

Repeat for each task. Keep it simple. The spec files provide the context.

### If Something Breaks

See `TESTING-GUIDE.md` for how to open the browser console and gather
error details. Then paste the error into Claude Code:

> I'm seeing this error in the browser console: [paste error]
> I think the issue is in [filename]. Can you investigate?

Pointing to the specific file saves time. If you don't know which file,
say so — but always include the console error.

### Backup Between Sessions

Before closing VS Code for the day, copy your project folder to a backup:

- Windows: Right-click folder → Copy → paste as `my-project-backup-feb26`
- This gives you a rollback point if the next session goes sideways

## Option 2: Cursor

**Requires:** Cursor installed, Cursor subscription

### Setup

1. Download from [cursor.com](https://cursor.com) if you don't have it
2. Create your project folder with the 5 spec files
3. Open the folder in Cursor: File → Open Folder

### Project Setup

1. Place your completed template files in the project root
2. Cursor reads rules from `.cursorrules` — create this file in your
   project root with the same content as `CLAUDE.md`
3. Rename it `.cursorrules`

### Using Cursor Composer

Press `Ctrl+I` (or `Cmd+I` on Mac) to open Composer. This is where
you'll work. Use the same prompt pattern:

> Read all .md files in this project. Execute Task 1 from tasks.md.
> Only Task 1.

Cursor also has inline editing (`Ctrl+K`) for targeted fixes, and a
chat panel (`Ctrl+L`) for questions without code changes.

### Agent Mode

Cursor's Agent mode (in Composer) can read files, run commands, and
make changes across multiple files. This is the closest to Claude Code's
workflow. Make sure Agent mode is selected (not "Normal" or "Ask").

## Option 3: Lovable

**Requires:** Lovable account (free tier works for prototyping)

### Setup

1. Go to [lovable.dev](https://lovable.dev)
2. Create a new project
3. Click the settings icon → "Project Knowledge"
4. Paste the contents of `rules.md` into the project knowledge field

### Uploading Spec Files

Lovable doesn't have a file system like VS Code. Instead:
1. Start a chat in your project
2. Upload your 5 spec files as attachments (drag and drop)
3. First message:

> Read all five attached files. These are the complete spec for this
> project. Confirm you understand, then execute Task 1 from tasks.md.
> Only Task 1.

### Lovable-Specific Notes

- Lovable creates its own file structure — you don't control it directly
- The preview panel shows your app live as it builds
- If the preview shows an error (orange bar), click "Try to fix" first
- For deeper debugging, right-click the preview → Inspect → Console
- Lovable has built-in version control — use "Revert" if a change breaks things

### Exporting from Lovable

To get your code out of Lovable (for GitHub or local editing):
1. Connect to GitHub via project settings
2. Lovable pushes your code to a repo automatically
3. Or download the project files directly from settings

## Which Tool Should I Pick?

| Scenario | Recommended Tool |
|---|---|
| You want full control over files | Claude Code or Cursor |
| You want the fastest prototype | Lovable |
| You've never used a code editor | Lovable (no editor needed) |
| You want to learn how the code works | Claude Code (read the output) |
| Your project needs a backend/database | Lovable (built-in Supabase) |
| You want to deploy a static site | Claude Code + Netlify drag-and-drop |

## Tool-Agnostic Tips

These apply regardless of which tool you use:

**One task at a time.** Don't say "build the whole app." Say "execute
Task 1." The spec files provide context — your prompt just points to
the next task.

**Read the agent output.** Don't just check if the code runs. Read
what the agent tells you about what it did and why. This is how you
learn what's happening without reading code.

**Test after every task.** Don't batch tasks together and test at the
end. Testing after each task catches problems when they're small and
easy to fix.

**Back up before risky changes.** Copy your project folder before
any task that touches multiple files or changes core logic. A 5-second
copy can save an hour of debugging.
