---
name: digital-design
description: >
  Design and build digital interfaces, web experiences, UI components, dashboards,
  motion graphics, and interactive prototypes. Use this skill whenever the user wants
  to create something that lives on a screen and responds to interaction — app screens,
  landing pages, dashboards, UI components, animated elements, or coded prototypes.
  Trigger on: "build a landing page", "design a dashboard", "create a UI component",
  "make an app screen", "animate this", "design a web page", "build an interface",
  "prototype this feature", "design a dark mode UI", or any request where the output
  is HTML/CSS/React or a detailed UI specification. Also trigger for data visualization
  requests that need interactive or screen-based output.
---

# Digital Design Skill

This skill governs screen-based design and frontend implementation. It covers four
sub-disciplines. Identify the right one from context, then execute with production-grade
code and intentional aesthetic decisions.

## Sub-Disciplines

| Sub-Discipline | Triggers | Primary Output |
|---|---|---|
| UI/UX Design | "app screen", "user flow", "wireframe", "prototype" | React/HTML + Spec |
| Web Design | "landing page", "website", "portfolio", "marketing site" | HTML/CSS/JS file |
| Dashboard & Data UI | "dashboard", "KPI", "chart", "analytics interface" | React + charting lib |
| Motion & Animation | "animate", "transition", "micro-interaction", "loading state" | HTML/CSS animation |

---

## Workflow

### Step 1 — Identify Sub-Discipline & Extract Context

Parse the request for:
- **Interface type**: What kind of screen is this?
- **Aesthetic direction**: Any style keywords? (dark mode, editorial, fintech, luxury, etc.)
- **Data / content**: What information does the interface display?
- **Interaction model**: Static? Hoverable? Animated? Clickable?
- **Tech constraint**: Plain HTML? React? Tailwind? No framework?

Default to React if no constraint is specified. Default to dark theme unless light is requested.

### Step 2 — Choose an Aesthetic Direction

Before writing code, commit to a clear visual direction. State it explicitly:

```
Aesthetic: [Name]
Palette: [Background] / [Surface] / [Text] / [Accent]
Typography: [Display face] + [Body face]
Motion: [None / Subtle / Expressive]
Distinguishing feature: [One thing that makes this unforgettable]
```

Avoid generic AI aesthetics. See `references/aesthetic-directions.md` for strong options.
**Never use**: Inter + purple gradient on white. Rounded-everything card soup. Generic
dashboard chrome. Overused hero sections with center-aligned H1 + subtitle + CTA button.

### Step 3 — Execute by Sub-Discipline

#### UI/UX DESIGN
- Build working code, not static mockups.
- Define component hierarchy before coding: what are the atoms, molecules, organisms?
- Use CSS custom properties for the design system (colors, spacing, type scale).
- Include hover states, focus states, and at least one animated transition.
- If producing a spec (not code): use the format in `references/ui-spec-template.md`.

#### WEB DESIGN
- Structure: clear visual hierarchy with one primary CTA per section.
- Above the fold: headline + subhead + visual. No more. Below fold: supporting content.
- Performance-conscious: no bloated libraries unless needed. Prefer CSS over JS for effects.
- Typography is the first tool. Set the type system before touching layout.
- Include responsive behavior: define what changes at 768px and 480px breakpoints.

#### DASHBOARD & DATA UI
- Data density is a feature, not a problem. Respect the user's intelligence.
- Hierarchy: KPI summary → trend visualization → detail table. Never bury the headline number.
- Charts: use Recharts (React) or D3 (vanilla). Never use Chart.js for design-forward work.
- Color in charts is semantic, not decorative. Positive = one color, negative = another.
- Numbers use monospaced font. Always. No exceptions.
- Reference Jing's domain: FP&A, trading, hospitality metrics — apply domain conventions.
- See `references/dashboard-patterns.md` for layout patterns and data conventions.

#### MOTION & ANIMATION
- CSS-only by default unless complexity demands JS.
- Timing: 150–200ms for micro-interactions. 300–500ms for page-level transitions. 
- Easing: ease-out for entrances, ease-in for exits, ease-in-out for state changes.
- Staggered reveals (animation-delay) for lists and grids — creates coherence.
- One well-orchestrated page load > many scattered micro-interactions.
- Export as standalone HTML file with embedded CSS animation.

### Step 4 — Code Quality Standards

- CSS custom properties for all design tokens (colors, spacing, type sizes).
- BEM or utility-class naming — be consistent, never mix.
- No inline styles except for dynamic values.
- Semantic HTML: use `<nav>`, `<main>`, `<section>`, `<article>` correctly.
- All interactive elements have keyboard focus styles.
- Comments on non-obvious design decisions.

### Step 5 — Deliver

1. The working code file (HTML or JSX)
2. A brief stating: aesthetic direction chosen, key decisions made, how to iterate
3. For dashboards: note the data schema expected (what props/variables to swap in)

---

## Tech Stack Reference

| Output Type | Stack | Notes |
|---|---|---|
| Landing page | HTML + CSS + vanilla JS | No framework needed |
| React component | React + Tailwind (core only) | Lucide icons available |
| Dashboard | React + Recharts | D3 for complex custom viz |
| Animation | HTML + CSS animation | Lottie if user has JSON |
| Interactive prototype | React with useState | Keep state minimal |

Available libraries in React artifacts:
`recharts`, `d3`, `lucide-react`, `lodash`, `mathjs`, `three` (r128)

---

## Files in This Skill

- `references/aesthetic-directions.md` — Named digital aesthetic families with palettes
- `references/dashboard-patterns.md` — Dashboard layout patterns and data conventions
- `references/ui-spec-template.md` — UI specification format (when code isn't the output)
- `references/animation-recipes.md` — CSS animation patterns ready to use
