---
name: visual-design
description: >
  Create original visual design work across illustration, brand identity, poster art,
  editorial graphics, and photo direction. Use this skill whenever the user wants to
  create a visual artifact — a poster, logo, illustration, brand kit, editorial graphic,
  art print, or any static visual piece intended to communicate through image and form.
  Trigger on phrases like: "design a poster", "create an illustration", "build a brand
  identity", "make a logo", "design something for me", "I need a visual", "art for my
  project", or any request where the primary deliverable is a crafted static image or
  visual system. Also trigger when the user describes a mood, aesthetic, or concept and
  asks Claude to express it visually.
---

# Visual Design Skill

This skill governs the creation of original visual work — static, crafted, image-led
design output. It covers four sub-disciplines. Read the context, identify the right
sub-discipline, then execute with the precision and craft of a senior designer.

## Sub-Disciplines

| Sub-Discipline | Triggers | Primary Output |
|---|---|---|
| Illustration | "illustrate", "draw", "editorial art", "character", "spot art" | PNG / PDF |
| Brand Identity | "logo", "brand kit", "identity system", "style guide" | SVG + PDF |
| Poster & Print Art | "poster", "print", "wall art", "gallery piece", "artwork" | PDF / PNG |
| Photo Direction | "retouch", "edit photo", "color grade", "art direct" | Edited image + brief |

---

## Workflow

### Step 1 — Identify Sub-Discipline & Extract Intent

Read the user's request carefully. Extract:
- **Subject**: What is being depicted or communicated?
- **Mood / Aesthetic**: Minimalist? Maximalist? Dark? Warm? Editorial?
- **Reference style**: Any artists, eras, or movements mentioned?
- **Deliverable format**: PNG, PDF, SVG, or descriptive brief?
- **Use context**: Social media? Print? Gallery? Brand application?

If the sub-discipline is ambiguous, ask one clarifying question before proceeding.

### Step 2 — Establish a Design Philosophy

Before executing, define a visual philosophy for this specific piece. This is NOT
a generic style description — it is a named aesthetic position for this work.

- **Name the movement** (1–2 words): e.g., "Chromatic Silence", "Brutalist Joy"
- **Write 2–3 sentences**: How do form, color, space, and type serve this philosophy?
- **State what is forbidden**: What would break the aesthetic? (e.g., "no gradients", "no drop shadows", "no centered layouts")

This philosophy governs every decision. If a choice doesn't serve it, reject the choice.

See `references/philosophy-examples.md` for philosophy templates by aesthetic family.

### Step 3 — Execute by Sub-Discipline

#### ILLUSTRATION
- Design must feel authored, not generated. Every element has intent.
- Favor geometric reduction over literal representation unless realism is requested.
- Limit color palette to 3–5 colors. Use flat fills or deliberate texture — not gradients.
- Text is minimal and integrated as a visual element, not a label.
- Output: PNG (high-res) or PDF.

#### BRAND IDENTITY
- Logo first: generate 3 distinct directions before converging on one.
- Each direction should represent a different strategic positioning (e.g., bold/geometric vs. refined/typographic vs. playful/illustrative).
- Color system: Primary (1), Secondary (1–2), Neutral (2), Semantic (optional).
- Typography: One display face + one body face. Specify weights and hierarchy.
- Deliver: Logo SVG + Color palette + Type spec + Usage rules (1-page PDF).
- See `references/brand-system-template.md` for the delivery format.

#### POSTER & PRINT ART
- Treat the page as a canvas, not a document. No default margins unless the design calls for them.
- Composition drives meaning: asymmetry, scale contrast, and negative space are tools.
- Typography is optional — if present, it is a graphic element, not a caption.
- Execute using the canvas-design approach: philosophy → visual expression → output.
- Output: PDF (print-ready, 300dpi equivalent) or PNG.

#### PHOTO DIRECTION
- Produce a creative brief, not an edited image (Claude cannot directly edit raster photos).
- Brief must include: Shot list, lighting direction, color grade reference, mood board description, post-processing instructions for Lightroom/Topaz/Luminar.
- If the user provides an image for analysis: describe what is working, what should change, and give specific Lightroom panel values (Exposure, Contrast, Highlights, Shadows, HSL).
- Output: Markdown brief + Lightroom preset recommendations.

### Step 4 — Craft Standards

These apply to ALL visual output from this skill:

- **No AI-generic aesthetics**: No purple-gradient-on-white. No stock-photo compositions. No overused type pairings (Inter + anything).
- **Intentionality over intensity**: A refined minimal piece and a dense maximalist piece are equally valid — what matters is that every choice is deliberate.
- **Craftsmanship**: Work must appear labored over. Spacing, alignment, color relationships — everything should feel considered. If something looks like a first draft, refine it.
- **Originality**: Never copy or closely reference existing artists' copyrighted work. Draw inspiration from movements, not individuals.

### Step 5 — Deliver

Always deliver:
1. The visual artifact (file or rendered output)
2. A 2–3 sentence design rationale explaining the key decisions
3. A note on how to extend or iterate (what to change if the user wants a different direction)

---

## Quick Reference: Aesthetic Families

| Family | Visual Signature | Avoid |
|---|---|---|
| Swiss / International | Grid, Helvetica/Neue Haas, red+black, strict hierarchy | Decoration, serifs |
| Editorial / Magazine | Asymmetry, large type, photography-led, white space | Symmetry, small type |
| Brutalist | Raw, heavy, overlapping, system fonts, high contrast | Polish, refinement |
| Japanese Minimalist | Negative space, single accent color, fine lines | Clutter, multiple colors |
| Art Deco / Geometric | Symmetry, gold, strong geometry, ornament | Organic shapes, informality |
| Psychedelic / Retro | Saturated, layered, hand-rendered feel, curves | Clean, modern |
| Luxury / Refined | Muted palette, premium type, restraint, texture | Brightness, clutter |

See `references/philosophy-examples.md` for detailed expressions of each family.

---

## Files in This Skill

- `references/philosophy-examples.md` — Named design philosophies by aesthetic family
- `references/brand-system-template.md` — Brand identity delivery format
- `references/color-systems.md` — Color theory and palette construction guide
- `assets/` — Font references and visual asset notes
