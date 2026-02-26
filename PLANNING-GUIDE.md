# Planning Guide

How to go from a vague idea to a buildable spec using these templates.

## The Core Principle

Spend 80% of your time planning, 20% building. This feels wrong when
AI agents can write code in seconds. But here's the thing: the agent
will build exactly what you describe. If your description is vague,
the output is vague. If your description is precise, the output is precise.

Planning isn't overhead. It's the product.

## Before You Touch the Templates

### Step 1: Brain dump

Open your AI tool in chat mode (not coding mode). Talk through your idea.
Don't worry about structure. Just explain what you want to build as if
you're telling a friend.

Good brain dump: "I want to build a tool that shows Latvian companies
how much they actually save when they donate to NGOs. They type in their
dividend amount and it shows the tax breakdown."

Bad brain dump: "Build me a tax calculator."

### Step 2: Get clarity through conversation

Stay in chat mode. Ask the AI to push back on your idea:

> "What questions would you need answered before you could build this?"

The AI will surface things you haven't thought about: edge cases,
formatting, error states, deployment. Write these down. You'll need
them for the templates.

### Step 3: Find references

Before building anything, find 1-2 examples of tools or sites that
feel like what you want. These can be:
- Screenshots from Mobbin or Dribbble (for design direction)
- Actual working tools you admire (for UX flow)
- Code snippets from component libraries (for specific UI elements)

You don't need all three. Even one reference screenshot gives the AI
agent more direction than a paragraph of description.

## Filling in the Templates

Work through them in this order. Don't skip ahead.

### 1. masterplan.md (30 minutes)

Start here. This is the "what and why" document.

**Key decisions to make:**
- What does the tool do in one sentence?
- Who is it for? (Be specific: "Latvian CFOs" not "business people")
- What does the user walk away with?

**The most important section:** Reference Test Case. If your project
involves any calculations, define ONE concrete example with known
correct values. Verify these values by hand or in a spreadsheet
before going further. Wrong numbers in the spec = wrong numbers in
the code.

### 2. design.md (20 minutes)

This is the "how it looks and feels" document.

**Key decisions to make:**
- Light or dark theme?
- What font? (System fonts are fine for v1)
- Single column or multi-column?
- What colors mean what? (Green = good, red = error, etc.)

**Tip:** If you have a design reference (from Step 3), paste the URL
into this doc. One screenshot communicates more than a full color palette.

### 3. implementation.md (40 minutes)

This is the "how it's built" document. This is where you'll spend
the most time.

**Key decisions to make:**
- What files exist and what's in each one?
- What are the element IDs? (Every element JS touches needs an ID)
- What's the calculation logic in plain English?
- What edge cases need handling?

**The section that prevents the most bugs:** Element ID table. List
every HTML element that JavaScript will read or write. Give each one
an ID. The agent uses this table to write code that matches your HTML.
Without it, the agent invents names and they won't match.

**The section most people skip (and shouldn't):** Edge Cases. What
happens when the user enters 0? Clears the field? Types letters?
Enters a very large number? Think through these now. Each one you
skip becomes a bug you'll spend tokens debugging later.

### 4. rules.md (15 minutes)

This is the "how the agent should behave" document.

**Essentials to include:**
- Read all docs before coding
- One task at a time
- No improvisation — don't add things not in the spec
- Report what you did and how to test it

**Paste your reference test case here too.** The agent checks its
work against these numbers. Having them in rules.md means they're
visible on every task.

**Start the "Lessons Learned" section empty.** You'll fill it in
during the build as you hit problems. This is one of the most
valuable sections — it prevents the same bug from happening twice.

### 5. tasks.md (30 minutes)

This is the "what to build in what order" document. Write this LAST
because it synthesizes everything above.

**Key principles:**
- Each task produces a testable result
- Foundation first (CSS, HTML skeleton), then logic, then UI, then polish
- Every task has a "Verify" checklist
- Include "No errors in browser console" in every verify step

**The dependency trap:** If Task 7 builds a function that calls
functions from Tasks 8 and 9, Task 7 must NOT include those calls.
Add them when the later tasks are completed. Otherwise, the agent
creates code that immediately throws a ReferenceError. State this
explicitly in the task description.

## Total Time: About 2-3 Hours

This feels like a lot. But consider what you're getting: a complete
spec that an AI agent can execute without you prompting, explaining,
or course-correcting at every step. The build phase becomes "proceed
with the next task" repeated until done.

Without planning, you'll spend those 2-3 hours anyway — on debugging,
re-prompting, reverting bad changes, and explaining context the agent
has already forgotten.

## Common Mistakes

**Writing tasks before the other docs.** You'll miss dependencies
and edge cases. Always write tasks last.

**Being vague in implementation.md.** "Add a nice chart" will produce
a random chart. "Add a two-column bar chart comparing tax-only vs
tax-plus-donation, with segments colored per design.md" will produce
what you actually want.

**Skipping the reference test case.** If your project has math, you
need numbers to check against. Without them, the agent might produce
plausible-looking but incorrect calculations and you won't catch it
until a user does.

**Forgetting locale formatting.** If your tool displays numbers
anywhere, define the exact format for every locale. The agent defaults
to US formatting (1,000.50) unless told otherwise. If your users are
European, this is wrong.

**Not defining what's out of scope.** AI agents love to help. If
you don't say "no user accounts, no analytics, no PDF export," the
agent may helpfully add these things. Be explicit about what you're
NOT building.
