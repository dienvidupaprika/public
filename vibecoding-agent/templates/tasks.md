# Tasks: [REPLACE: Project Name]

## How to Use This File

This is the single source of truth for what gets built and in what order.
Each task is atomic — it produces a testable result. The agent reads this
file before each task and executes ONLY the next incomplete task.

Mark tasks complete as you go: change `[ ]` to `[x]`.

<!-- QUESTION: Before writing tasks, make sure you've completed:
- masterplan.md (what you're building)
- design.md (how it looks)
- implementation.md (how it's built)
- rules.md (agent constraints)

Tasks are the LAST document you write. They synthesize everything above
into an ordered checklist. If you write tasks before the other docs,
you'll miss things and need to rewrite. -->

---

## Phase 1: Foundation

<!-- QUESTION: What needs to exist before anything functional can work?
Usually: the CSS file with base styles, the HTML skeleton with all
element IDs, and the project structure. -->

### Task 1: [REPLACE: e.g., "Create styles.css with design tokens and base layout"]

**What to build:**
- [REPLACE: Specific deliverables — what the file should contain]
- [REPLACE: Reference design.md for colors, fonts, spacing]

**Files created:** [REPLACE: e.g., `styles.css`]

**Verify:**
- [ ] File exists and is not empty
- [ ] [REPLACE: e.g., "Open in browser — page has correct background color and font"]
- [ ] No errors in browser console (F12 → Console tab)

---

### Task 2: [REPLACE: e.g., "Create index.html with full page structure"]

**What to build:**
- [REPLACE: Specific deliverables]
- [REPLACE: Every element ID from implementation.md must be present]

**Files created:** [REPLACE: e.g., `index.html`]

**Verify:**
- [ ] File opens in browser without errors
- [ ] [REPLACE: e.g., "All sections visible in correct order"]
- [ ] [REPLACE: e.g., "Results section is hidden (empty state)"]
- [ ] No errors in browser console

---

## Phase 2: Core Logic

<!-- QUESTION: What is the engine of your project?
Build the calculation/logic layer BEFORE the UI layer.
This means the functions exist and can be tested, even if the UI
doesn't call them yet.

IMPORTANT: If Task N builds a function that calls functions from
later tasks, Task N must NOT include those calls yet. Add them when
the later task is built. Otherwise the agent creates code that
immediately breaks with a ReferenceError. -->

### Task 3: [REPLACE: e.g., "Add constants and core calculation function to app.js"]

**What to build:**
- [REPLACE: Specific deliverables]
- Reference: implementation.md "Constants Block" and "Core Logic Function"

**Files created/modified:** [REPLACE: e.g., `app.js` (new)]

**Verify:**
- [ ] File exists
- [ ] [REPLACE: e.g., "Open browser console, type: `calculate(100000, 7500)` — verify output matches reference case from rules.md"]
- [ ] No errors in browser console

<!-- QUESTION: Can you verify core logic independently from the console?
If yes, write the exact console command in the verify step.
If no, you may need to temporarily expose the function on `window`. -->

---

### Task 4: [REPLACE: e.g., "Add formatting and parsing utility functions"]

**What to build:**
- [REPLACE: Specific deliverables]

**Files modified:** [REPLACE: e.g., `app.js`]

**Verify:**
- [ ] [REPLACE: e.g., "Console test: `formatCurrency(1234.5, 'en')` returns '€1,234.50'"]
- [ ] [REPLACE: e.g., "Console test: `formatCurrency(1234.5, 'lv')` returns '1 234,50 €'"]
- [ ] No errors in browser console

---

## Phase 3: UI Wiring

<!-- QUESTION: Now connect the logic to the page. Each task should wire
up one section of the UI and produce a visible, testable result. -->

### Task 5: [REPLACE: e.g., "Wire up input field and show results on input"]

**What to build:**
- [REPLACE: Specific deliverables]
- [REPLACE: What event listeners to attach]
- [REPLACE: What should update when the user types]

**Files modified:** [REPLACE: e.g., `app.js`]

**Verify:**
- [ ] [REPLACE: e.g., "Type 100000 → results section appears with correct values"]
- [ ] [REPLACE: e.g., "Clear input → results section hides"]
- [ ] No errors in browser console

---

### Task 6: [REPLACE: continue with remaining UI tasks]

[REPLACE: Follow the same pattern for each task]

---

## Phase 4: Polish

<!-- QUESTION: What makes this feel finished rather than a prototype?
Common polish tasks: transitions, mobile responsiveness, copy-to-clipboard,
visual refinements. -->

### Task N: [REPLACE: e.g., "Add transitions and visual polish"]

[REPLACE: Follow the same pattern]

---

### Task N+1: [REPLACE: e.g., "Mobile responsive adjustments"]

**Verify:**
- [ ] Resize browser to 375px wide — no horizontal scrollbar
- [ ] All buttons and inputs are usable at touch size (min 44px)
- [ ] Text is readable without zooming

---

## Phase 5: Multi-language (if applicable)

<!-- QUESTION: Delete this phase if single-language.
If multilingual: build the primary language first (Phases 1-4),
then duplicate and translate. This avoids maintaining two files
in parallel during the build. -->

### Task N+2: [REPLACE: e.g., "Create second language version"]

**What to build:**
- Duplicate [REPLACE: e.g., `index.html`] as [REPLACE: e.g., `eng.html`]
- Translate all visible text
- Update language toggle links in both files
- Update `window.TEXT` object for JS strings

**Verify:**
- [ ] Both pages load without errors
- [ ] Language toggle switches between pages correctly
- [ ] Number formatting matches each locale
- [ ] No English text on non-English page (and vice versa)

---

## Phase 6: Ship

### Task N+3: [REPLACE: e.g., "Create README.md with deploy instructions"]

**What to build:**
- How to deploy (drag-and-drop to Netlify or equivalent)
- How to update content that might change (tax rates, text, etc.)
- File structure explanation

**Verify:**
- [ ] A person who didn't build this can follow the deploy steps
- [ ] The "how to update" section points to correct line numbers

---

### Task FINAL: End-to-End Verification

**Do not skip this. Open the project in a browser and test everything:**

- [ ] Page loads with correct empty state
- [ ] [REPLACE: primary user flow — input → output → verify values]
- [ ] [REPLACE: edge case — minimum input]
- [ ] [REPLACE: edge case — zero input]
- [ ] [REPLACE: any interactive elements — toggles, sliders, buttons]
- [ ] [REPLACE: copy/share functionality]
- [ ] [REPLACE: language switching if applicable]
- [ ] [REPLACE: mobile layout at 375px]
- [ ] Tab through all elements — focus visible on each
- [ ] No errors in browser console throughout entire test
- [ ] Total file size: all files combined under [REPLACE: e.g., 50KB]
