# Implementation Plan: [REPLACE: Project Name]

## Architecture Overview

This is a [REPLACE: e.g., "static site with vanilla HTML, CSS, and JavaScript — no framework, no build step, no backend"].

<!-- QUESTION: Do you actually need a framework (React, Vue, Svelte)?
For tools, calculators, landing pages, and most internal apps: NO.
Vanilla HTML/CSS/JS means:
- Any AI agent can build it without configuration
- No npm, no build step, no node_modules
- Opens directly in a browser by double-clicking the HTML file
- Deploys by dragging a folder to Netlify

Use a framework only if you need: complex state management, routing
between many views, or real-time data updates. -->

## File Structure

```
[REPLACE: project-name]/
├── index.html          ← [REPLACE: e.g., "Main page (Latvian)"]
├── [REPLACE].html      ← [REPLACE: e.g., "English version" — delete if single-language]
├── styles.css          ← All styles, single file
├── [REPLACE: app].js   ← All logic, single file
└── README.md           ← Deploy instructions and maintenance notes
```

<!-- QUESTION: Can your entire project fit in these files? The fewer files,
the less the AI agent needs to read on each task, the better its output.
One CSS file. One JS file. One HTML per language. That's it for most projects. -->

## HTML Structure

### Page Sections (in DOM order)

1. **[REPLACE: e.g., Language toggle]** — [REPLACE: what it contains]
2. **[REPLACE: e.g., Header]** — [REPLACE: title, subtitle, explainer text]
3. **[REPLACE: e.g., Input section]** — [REPLACE: what inputs, what types]
4. **[REPLACE: e.g., Results section]** — [REPLACE: what displays here]
5. **[REPLACE: e.g., Footer]** — [REPLACE: disclaimer, sources]

### Element IDs

Define every element the JavaScript will need to reference:

| ID | Element | Purpose |
|---|---|---|
| [REPLACE: e.g., `dividend-input`] | `<input>` | [REPLACE: e.g., "Main number input"] |
| [REPLACE: e.g., `results-section`] | `<section>` | [REPLACE: e.g., "Container for all results, hidden until input"] |

<!-- QUESTION: List EVERY element that JavaScript will read from or write to.
If you miss one, the agent will invent an ID name and it may not match
your HTML. This table prevents that mismatch. -->

## CSS Architecture

### Approach
[REPLACE: e.g., "Vanilla CSS with CSS custom properties (variables) for colors. No preprocessor. No Tailwind. Mobile-first with one breakpoint at 768px."]

### Key Classes

| Class | Purpose |
|---|---|
| `.hidden` | `display: none` — used by JS to show/hide sections |
| [REPLACE: e.g., `.input-group`] | [REPLACE: purpose] |
| [REPLACE: e.g., `.results-section`] | [REPLACE: purpose] |

### State Classes
- `.hidden` — element not visible
- [REPLACE: e.g., `.hint-optimal` — green styling for positive state]
- [REPLACE: e.g., `.hint-warning` — amber styling for suboptimal state]

## JavaScript Architecture

### No Framework. Single File. Sections in This Order:

1. **Constants** — All magic numbers, tax rates, thresholds at the top
2. **Core logic** — Pure functions that take input, return output (no DOM)
3. **Utility functions** — Formatting, parsing, helpers
4. **UI controller** — DOM references, event listeners, update functions
5. [REPLACE: additional sections if needed]

<!-- QUESTION: Why this order? Constants first means they're easy to find
and change. Core logic second means it can be tested independently.
UI controller last means it ties everything together.
The agent should build these in this order too — see tasks.md. -->

### Constants Block

```javascript
// === CONSTANTS ===
const [REPLACE: RATE_NAME] = [REPLACE: value]; // [REPLACE: what this is]
const [REPLACE: RATE_NAME] = [REPLACE: value]; // [REPLACE: what this is]
```

<!-- QUESTION: List EVERY number that might change in the future.
Tax rates change. Thresholds change. Percentages change.
If it's a number and it's not purely mathematical (like dividing by 2
to find a midpoint), it belongs in constants. -->

### Core Logic Function

```
Input:  [REPLACE: e.g., "dividendAmount (number), donationAmount (number)"]
Output: [REPLACE: e.g., "object with baseTax, relief, netCost, discount, etc."]
```

The function should be pure — no DOM access, no side effects. It takes
numbers in and returns numbers out. This makes it testable.

<!-- QUESTION: Write out the calculation steps in pseudocode:
Step 1: [REPLACE]
Step 2: [REPLACE]
Step 3: [REPLACE]
...

If you can't write the steps clearly in English, the agent can't write
them clearly in code. This is where most calculation bugs originate. -->

### Formatting Functions

<!-- QUESTION: Does your project display formatted numbers? If yes, define:
- How does formatCurrency work for each locale?
- How does the input field parse user-typed numbers?
  (Users might type "1,000" or "1.000" or "1 000" depending on locale)
- What happens if the user types letters or symbols? -->

### UI Controller

The `init()` function should:
1. Grab all DOM elements by ID (from the table above)
2. Attach event listeners
3. [REPLACE: any initial state setup]

<!-- QUESTION: What events trigger recalculation?
- Input field change? (use 'input' event, not 'change')
- Slider movement? (use 'input' event)
- Button click?
List every event → element → handler connection. -->

## Edge Cases to Handle

<!-- QUESTION: What happens when...
- The user enters 0? → [REPLACE: expected behavior]
- The user enters a very small number (e.g., 1)? → [REPLACE]
- The user enters a very large number (e.g., 999,999,999)? → [REPLACE]
- The user clears the input entirely? → [REPLACE]
- The user pastes text instead of a number? → [REPLACE]

Think through these NOW. Each one you skip becomes a bug report later. -->

## What This Project Does NOT Include

- [REPLACE: e.g., "No backend, no database, no user accounts"]
- [REPLACE: e.g., "No analytics or tracking"]
- [REPLACE: e.g., "No PDF export — just clipboard copy"]

<!-- QUESTION: Listing what's OUT of scope is as important as listing what's
in scope. It prevents the AI agent from helpfully adding features you
didn't ask for. -->
