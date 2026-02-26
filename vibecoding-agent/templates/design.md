# Design Guidelines: [REPLACE: Project Name]

## Design Philosophy

[REPLACE: One sentence about how this should feel. Example: "A tool that a
Latvian CFO would trust enough to show their board."]

<!-- QUESTION: Who is looking at this? A developer? An executive? A teenager?
Your audience determines everything below. A tool for accountants needs
different typography than a tool for gamers. -->

## Color Palette

### Primary Colors
- Background: [REPLACE: e.g., #FFFFFF or #0F172A]
- Text: [REPLACE: e.g., #1E293B]
- Accent / interactive: [REPLACE: e.g., #2563EB]

### Semantic Colors
- Success / positive: [REPLACE: e.g., #16A34A]
- Warning: [REPLACE: e.g., #F59E0B]
- Error: [REPLACE: e.g., #DC2626]
- Muted / secondary text: [REPLACE: e.g., #64748B]

<!-- QUESTION: Are you using a light or dark theme? Pick one. Don't build
both for v1. If unsure, use light — it's safer for professional tools. -->

## Typography

- Font family: [REPLACE: e.g., "DM Sans" from Google Fonts, or "system-ui" for no external dependency]
- Base size: [REPLACE: e.g., 16px]
- Headings: [REPLACE: e.g., 700 weight, 1.5rem / 1.25rem / 1rem]
- Body: [REPLACE: e.g., 400 weight, 1rem, line-height 1.6]

<!-- QUESTION: Do you actually need a custom font? Google Fonts adds a network
request. System fonts (system-ui, -apple-system) load instantly and look
professional. Only use a custom font if design quality demands it. -->

## Layout

- Max container width: [REPLACE: e.g., 640px for a single-column tool, 1200px for a dashboard]
- Padding: [REPLACE: e.g., 24px on desktop, 16px on mobile]
- Section spacing: [REPLACE: e.g., 32px between major sections]

<!-- QUESTION: Is this a single-column layout or multi-column?
Single-column is easier to make responsive and harder to get wrong.
Use multi-column only if you have side-by-side comparison or a dashboard. -->

## Components

### Inputs
- Style: [REPLACE: e.g., "bordered input fields with a prefix label inside"]
- Border radius: [REPLACE: e.g., 8px]
- Focus state: [REPLACE: e.g., "blue ring, 2px solid accent color"]

### Buttons
- Primary: [REPLACE: e.g., "filled accent color, white text, 8px radius"]
- Secondary: [REPLACE: e.g., "outlined, accent border, transparent background"]

### Cards / Sections
- Background: [REPLACE: e.g., "subtle gray #F8FAFC with 1px border"]
- Border radius: [REPLACE: e.g., 12px]
- Shadow: [REPLACE: e.g., "none" or "0 1px 3px rgba(0,0,0,0.1)"]

## Animations and Transitions

<!-- QUESTION: Do you need animations? They add polish but also complexity.
For v1, simple fade-ins and transitions are enough. Skip anything that
requires a library (Framer Motion, GSAP) unless design is your differentiator. -->

- Transitions: [REPLACE: e.g., "all 0.3s ease on interactive elements"]
- Reveal animations: [REPLACE: e.g., "sections fade in when they become relevant"]

## Responsive Behavior

- Breakpoint: [REPLACE: e.g., 768px — below this is "mobile"]
- Mobile changes: [REPLACE: e.g., "single column, larger touch targets, stacked layout"]

<!-- QUESTION: Test your design on 375px wide (iPhone SE). If elements
overflow or text becomes unreadable, the layout needs work.
Define what changes at mobile size NOW, not after the build. -->

## Number and Currency Formatting

<!-- QUESTION: Skip this section if your project doesn't display numbers.
If it does, this is CRITICAL. AI agents will default to US formatting
(1,000.50) unless you specify otherwise. -->

| Element | English Format | [REPLACE: Other Locale] Format |
|---|---|---|
| Thousands separator | , (comma) | [REPLACE: e.g., space] |
| Decimal separator | . (period) | [REPLACE: e.g., comma] |
| Currency symbol | €100 (before) | [REPLACE: e.g., 100 € (after)] |
| Example | €1,000.50 | [REPLACE: e.g., 1 000,50 €] |

## Accessibility Minimums

- All interactive elements must be reachable by Tab key
- Focus states must be visible (not just browser default)
- Color contrast: text on background must meet WCAG AA (4.5:1 ratio)
- Use `aria-live="polite"` on any section that updates dynamically

<!-- QUESTION: Will screen reader users need this tool? If there's any chance:
add aria-labels to charts, icons, and any element where meaning comes from
visuals rather than text. Define these now, not as a polish step. -->

## Design References

[REPLACE: Link screenshots, Dribbble shots, Mobbin examples, or existing
tools that capture the feel you want. Even one screenshot gives the AI
agent more clarity than 500 words of description.]

- Reference 1: [REPLACE: URL or "see attached screenshot"]
- Reference 2: [REPLACE: URL]
