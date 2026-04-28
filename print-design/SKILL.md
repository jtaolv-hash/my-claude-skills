---
name: print-design
description: >
  Design print-ready and document-based deliverables: editorial layouts, pitch decks,
  brand guides, annual reports, packaging concepts, and formatted documents. Use this
  skill whenever the user wants a deliverable that is file-based and formatted —
  a PDF, PPTX, DOCX, or print-ready design artifact. Trigger on: "create a pitch deck",
  "design a report", "make a brochure", "layout a document", "build a brand guidelines
  doc", "design packaging", "create a one-pager", "make a presentation", "format this
  into a PDF", or any request where the final output is a structured, paginated, or
  print-ready file. Also trigger when the user needs to turn content (data, copy, ideas)
  into a designed document or professional deliverable.
---

# Print Design Skill

This skill governs the creation of designed, file-based deliverables. It covers
documents, decks, editorial layouts, packaging, and formatted reports. The output
is always a real file the user can use or send.

## Sub-Disciplines

| Sub-Discipline | Triggers | Primary Output |
|---|---|---|
| Pitch Decks & Presentations | "deck", "slides", "pitch", "presentation" | PPTX |
| Reports & Documents | "report", "white paper", "brand guide", "memo" | DOCX or PDF |
| Editorial Layout | "magazine spread", "editorial", "publication", "book" | PDF |
| Packaging | "packaging", "label", "box design", "product wrap" | PDF concept |
| One-pagers & Collateral | "one-pager", "sell sheet", "flyer", "brochure" | PDF |

---

## Workflow

### Step 1 — Identify Deliverable Type & Context

Extract from the request:
- **File type needed**: PPTX, DOCX, PDF?
- **Audience**: Internal? Investor? Client? Consumer?
- **Content available**: Does the user have copy/data to format, or does Claude generate it?
- **Brand context**: Any existing colors, fonts, or style to match?
- **Length/scope**: How many slides, pages, or sections?

If content is not provided, ask: "Do you have the content to drop in, or should I generate placeholder content with the layout?"

### Step 2 — Read the Relevant Skill

Before creating any file, read the appropriate public skill:

| Output | Read first |
|---|---|
| PPTX | `/mnt/skills/public/pptx/SKILL.md` |
| DOCX | `/mnt/skills/public/docx/SKILL.md` |
| PDF | `/mnt/skills/public/pdf/SKILL.md` |

These skills contain environment-specific constraints, libraries, and output paths.
**Always read the relevant SKILL.md before writing any code.**

### Step 3 — Design the Visual System

Even for document deliverables, establish a design system before executing:

```
Color system:   Primary / Secondary / Text / Background / Accent
Typography:     Display face (slides/headers) + Body face (body copy)
Grid:           Column count + margin width + gutter
Visual language: Photography? Illustration? Data viz? Geometric elements?
Tone:           Formal? Approachable? Authoritative? Creative?
```

See `references/document-design-systems.md` for pre-built systems by document type.

### Step 4 — Execute by Sub-Discipline

#### PITCH DECKS (PPTX)
Follow the PPTX skill exactly. Key principles:
- Slide structure: Problem → Solution → Why now → Market → Product → Traction → Team → Ask
- One idea per slide. Never more than 40 words of body copy on a slide.
- Data slides: one chart, one insight label in large type, one takeaway sentence.
- Design: dark or high-contrast preferred for projector contexts.
- See `references/deck-structures.md` for slide-by-slide templates by deck type.

#### REPORTS & DOCUMENTS (DOCX)
Follow the DOCX skill exactly. Key principles:
- Hierarchy: use Word styles (Heading 1–3) — never manually sized text.
- Visual breaks: pull quotes, data callouts, and dividers prevent wall-of-text fatigue.
- Tables for all comparative data. Never use bullet points where a table would be clearer.
- Page numbers, headers/footers, and a table of contents for documents > 8 pages.

#### EDITORIAL LAYOUT (PDF)
- Treat each page as a composition, not a container.
- Establish a baseline grid and stick to it.
- Image placement: bleed images to the edge when they're the hero. Float images in text when they're supporting.
- Typography is the primary design tool. Set the type system first.
- Output via the PDF skill — generate Python/reportlab code for the layout.

#### PACKAGING (PDF Concept)
- Claude produces a flat design concept, not a dieline-ready production file.
- Front panel is the primary canvas — design it first, then extend to back/side.
- Hierarchy: Brand name → Product name → Key claim → Supporting info → Legal
- Consider: How does this look on a shelf at thumbnail size? At 2 feet away?
- Output: PDF showing front panel + back panel + color/type specifications.

#### ONE-PAGERS & COLLATERAL (PDF)
- Single page = single idea. Define the one thing the reader must take away.
- Visual structure: Hook (top) → Supporting detail (middle) → CTA (bottom).
- White space is not wasted space — it directs the eye.
- Output: PDF via the PDF skill.

### Step 5 — Craft Standards for Print

- **Hierarchy is everything**: The reader's eye must know where to go first, second, third.
- **Consistency**: Same margin, same spacing unit, same color usage throughout.
- **Typography first**: Set the type before touching any other design element.
- **Never use default styles**: Word's default Normal style, PowerPoint's default text boxes — always override.
- **Every page has a purpose**: If a page or section doesn't earn its place, cut it.

### Step 6 — Deliver

1. The designed file (copied to `/mnt/user-data/outputs/`)
2. A brief: what design decisions were made and why
3. What to change if they want a different direction (e.g., "for a lighter feel, swap to the Editorial Light palette")

---

## Files in This Skill

- `references/document-design-systems.md` — Pre-built visual systems by document type
- `references/deck-structures.md` — Slide-by-slide templates for common deck types
- `references/typography-for-print.md` — Type scale and pairing guide for documents
