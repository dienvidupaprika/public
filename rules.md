# Rules: [REPLACE: Project Name]

These rules govern agent behavior throughout the build. The agent must
read this file before every task.

## Golden Rules

1. **Read before you act.** Read all .md files before writing any code.
   Read tasks.md to find the current task. Execute ONLY that task.

2. **One task at a time.** Do not combine tasks. Do not skip ahead.
   Do not start the next task without being told to proceed.

3. **No improvisation.** Do not add features, styles, or functionality
   not specified in the planning documents. If something seems missing,
   ask — don't guess.

4. **Report what you did.** After completing a task, state:
   - What files you created or modified
   - What the user should test
   - Any concerns or decisions you made

<!-- QUESTION: Are there any project-specific rules to add? Examples:
- "Never use external libraries unless specified in implementation.md"
- "All text content must come from the HTML, not hardcoded in JavaScript"
- "Do not modify any file outside the project folder" -->

## Code Standards

### HTML
- Semantic elements where appropriate (`<header>`, `<section>`, `<footer>`)
- Every element referenced by JS must have the exact ID from implementation.md
- [REPLACE: any additional HTML rules for your project]

### CSS
- No `!important` unless overriding third-party styles
- Use CSS custom properties for colors (defined once, used everywhere)
- Mobile styles via `@media (max-width: [REPLACE: breakpoint]px)`
- [REPLACE: any additional CSS rules]

### JavaScript
- `'use strict';` at the top of the file
- Constants in UPPER_SNAKE_CASE at the top
- No global variables beyond the constants block
- Wrap everything in a DOMContentLoaded listener or init function
- [REPLACE: any additional JS rules]

## Formatting and Locale Rules

<!-- QUESTION: Delete this section if your project doesn't format numbers.
If it does, these rules prevent the most common bug: wrong number format. -->

- [REPLACE: e.g., "English locale: €1,234.56 (symbol before, comma thousands, dot decimal)"]
- [REPLACE: e.g., "Latvian locale: 1 234,56 € (space thousands, comma decimal, symbol after)"]
- [REPLACE: e.g., "The input field must accept both comma and dot as decimal separators"]

## Task Dependencies

<!-- QUESTION: Are there tasks where the order matters for correctness?
For example: if Task 7 builds a function that calls functions from
Tasks 8 and 9, Task 7 must NOT call those functions yet.
State this explicitly or the agent will call functions that don't exist. -->

[REPLACE: List any dependency notes, or write "Tasks are independent
within each phase — execute in order from tasks.md."]

## Verification Reference Case

<!-- QUESTION: If your project involves calculations, paste the reference
case from masterplan.md here too. The agent will check its work against
these numbers. -->

Test input: [REPLACE: e.g., "Dividend = 100,000, Donation = 7,500"]
Expected output:
- [REPLACE: e.g., "Base tax = 25,000"]
- [REPLACE: e.g., "Tax after relief = 18,906.25"]
- [REPLACE: e.g., "Net cost = 1,406.25"]

## Known Limitations

<!-- QUESTION: What CAN'T the agent see or test? List these so you
remember to test them manually. Common examples: -->

- [REPLACE: e.g., "Clipboard copy requires HTTPS or localhost — won't work from file:// protocol"]
- [REPLACE: e.g., "Slider appearance varies by browser and OS"]
- [REPLACE: e.g., "Font loading depends on Google Fonts availability"]

## Lessons Learned

<!-- This section starts empty. As you build and hit problems, add notes
here so the agent doesn't repeat mistakes. Example entries:

- "Setting slider .value programmatically does NOT fire the input event.
  Do NOT use dispatchEvent — it causes double calculation."
- "When the donation cap is not a round number (e.g., 7.50), the slider
  step size must be small enough to reach the exact cap value."

After each debugging session, ask the agent: "What should I add to
rules.md so this doesn't happen again?" Then paste its answer here. -->
