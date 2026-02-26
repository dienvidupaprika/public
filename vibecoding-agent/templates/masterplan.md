# Masterplan: [REPLACE: Project Name]

## What This Is

[REPLACE: One sentence. What does this tool/app do?]

[REPLACE: One sentence. Who is it for?]

[REPLACE: One sentence. Why does it need to exist? What's the alternative today?]

<!-- QUESTION: Can you explain this project to someone in 30 seconds without
using jargon? If not, simplify until you can. That explanation IS your masterplan. -->

## The Problem

[REPLACE: What is the user currently doing instead? What's painful about it?]

<!-- QUESTION: Have you personally experienced this problem, or are you
assuming others have it? If you haven't, talk to 2-3 people who have
before writing the rest of this document. -->

## How It Works (User Perspective)

1. User arrives at [REPLACE: landing page / app / tool]
2. User [REPLACE: first action — what do they see and do?]
3. [REPLACE: what happens next — what does the tool show them?]
4. User [REPLACE: final action — what do they leave with?]

<!-- QUESTION: Is this a single-page tool or a multi-page app?
Single-page is dramatically simpler to build and maintain.
If you're tempted to add pages, ask: can this be one page with sections? -->

## Core Requirements

### Must Have (ship-blocking)
- [REPLACE: Feature 1 — be specific about what it does, not how]
- [REPLACE: Feature 2]
- [REPLACE: Feature 3]

### Nice to Have (post-launch)
- [REPLACE: Feature that can wait]

<!-- QUESTION: For each "must have" — if you removed it, would the tool still
solve the core problem? If yes, move it to "nice to have." Ruthlessly cut
scope. You can always add features later. You cannot easily remove complexity. -->

## Domain-Specific Knowledge

<!-- QUESTION: Does your project involve any of these? Check all that apply
and fill in the relevant sections:

[ ] Calculations or formulas — define them precisely below
[ ] Legal/regulatory rules — cite the specific law or regulation
[ ] Multiple languages — list languages and formatting differences
[ ] External data sources — list APIs or data you'll need
[ ] User accounts / authentication — describe what's needed
[ ] Payments — describe what's needed

If NONE of these apply, delete this section. -->

### Calculations / Formulas
[REPLACE: Write out every formula in plain language. Example:
"Tax = (Dividend ÷ 0.8) × 0.2. The donation cap is 30% of this tax amount."
Do NOT leave any formula ambiguous. The agent will guess wrong.]

### Reference Test Case
[REPLACE: Pick one concrete example with known correct values. Example:
"If dividend = 100,000 then tax = 25,000, cap = 7,500..."
This becomes your verification checkpoint throughout the build.]

<!-- QUESTION: Can you verify your reference case by hand or with a
spreadsheet BEFORE the build starts? Do it now. If the numbers are
wrong in the spec, they'll be wrong in the code. -->

### Legal / Regulatory Sources
- [REPLACE: Link to the law, regulation, or official source]
- [REPLACE: Date of the version you're referencing]

### Language / Locale Requirements
<!-- QUESTION: If bilingual/multilingual:
- Which language is the default landing page?
- How do numbers format in each locale? (e.g., 1,000.50 vs 1 000,50)
- Where does the currency symbol go? (€100 vs 100 €)
- Will you need a native speaker to review the translations? Plan for this. -->

## Design Direction

The design should feel [REPLACE: 2-3 adjectives — e.g., "professional, minimal, trustworthy"].

For exact design parameters, see `design.md`.

## Technical Approach

This will be built as [REPLACE: e.g., "a static HTML/CSS/JS site with no backend"
or "a React app with Supabase backend" or "a Lovable project"].

For implementation details, see `implementation.md`.

## Deployment

Deploy to [REPLACE: Netlify / Vercel / Lovable hosting / other].

Target URL: [REPLACE: your-project.netlify.app or similar]

<!-- QUESTION: Do you need a custom domain? If not, don't set one up now.
Ship first, polish later. -->

## Success Criteria

This project is done when:
- [ ] [REPLACE: A user can do X without help]
- [ ] [REPLACE: The reference test case produces correct results]
- [ ] [REPLACE: It works on mobile]
- [ ] [REPLACE: It passes the final verification checklist in tasks.md]

## File References

| Document | Purpose |
|---|---|
| `design.md` | Visual design, colors, typography, layout |
| `implementation.md` | Technical architecture, file structure, code patterns |
| `rules.md` | Agent behavior constraints |
| `tasks.md` | Ordered build checklist |
