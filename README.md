# Creative Skills — Jing's Design Stack

Four custom SKILL.md files covering Visual, Digital, Print, and Generative design.
Built to slot into the existing `jtaolv-hash/my-claude-skills` GitHub skill library.

---

## Skills Overview

| Skill | Trigger words | Output formats | Core tools |
|---|---|---|---|
| `visual-design` | poster, logo, illustration, brand identity, art | PNG, PDF, SVG | canvas-design, svg-logo |
| `digital-design` | landing page, dashboard, UI, app screen, animate | HTML, JSX, React | frontend-design, Recharts |
| `print-design` | deck, report, brochure, packaging, one-pager | PPTX, DOCX, PDF | pptx/docx/pdf skills |
| `generative-design` | flow field, particle, data viz, generative pattern | HTML+p5.js, JSX | algorithmic-art, D3 |

---

## Directory Structure

```
creative-skills/
├── README.md                          ← this file
├── visual-design/
│   ├── SKILL.md
│   └── references/
│       ├── philosophy-examples.md     ← aesthetic families & design laws
│       ├── brand-system-template.md   ← brand identity delivery format
│       └── color-systems.md           ← (add: color theory reference)
├── digital-design/
│   ├── SKILL.md
│   └── references/
│       ├── aesthetic-directions.md    ← named palettes by context
│       ├── dashboard-patterns.md      ← FP&A/trading/hospitality UI patterns
│       ├── ui-spec-template.md        ← (add: UI spec format)
│       └── animation-recipes.md       ← (add: CSS animation patterns)
├── print-design/
│   ├── SKILL.md
│   └── references/
│       ├── document-design-systems.md ← pre-built systems by doc type
│       ├── deck-structures.md         ← (add: slide-by-slide templates)
│       └── typography-for-print.md    ← (add: type scale guide)
└── generative-design/
    ├── SKILL.md
    └── references/
        ├── generative-philosophy.md   ← algorithmic aesthetic movements
        ├── viz-decision-guide.md      ← chart type selection guide
        ├── p5-patterns.md             ← (add: p5.js pattern templates)
        └── image-gen-prompts.md       ← (add: AI image prompt templates)
```

---

## Installation (Claude Code)

### Option A — Add to existing GitHub skill library

```bash
# Clone your skill library
git clone https://github.com/jtaolv-hash/my-claude-skills
cd my-claude-skills

# Copy the creative skills in
cp -r /path/to/creative-skills/visual-design ./
cp -r /path/to/creative-skills/digital-design ./
cp -r /path/to/creative-skills/print-design ./
cp -r /path/to/creative-skills/generative-design ./

# Commit and push
git add .
git commit -m "feat: add 4 creative design skills"
git push
```

### Option B — Add to Claude Code project directly

```bash
# From your project root
mkdir -p .claude/skills
cp -r /path/to/creative-skills/* .claude/skills/
```

### Option C — Global user skills

```bash
# macOS/Linux
mkdir -p ~/.claude/skills
cp -r /path/to/creative-skills/* ~/.claude/skills/

# Windows (PowerShell)
New-Item -ItemType Directory -Force "$env:APPDATA\Claude\skills"
Copy-Item -Recurse creative-skills\* "$env:APPDATA\Claude\skills\"
```

---

## How Skills Trigger

Claude loads only the `name` and `description` from SKILL.md frontmatter at startup.
When your message matches a skill's description, Claude loads the full SKILL.md.

**Visual-design** triggers on: poster, logo, illustration, brand kit, art print, editorial graphic, visual, style guide, identity system, photo direction

**Digital-design** triggers on: landing page, web design, UI, app screen, dashboard, chart (when interactive), animate, component, prototype, interface

**Print-design** triggers on: deck, slides, pitch, report, annual report, brochure, packaging, one-pager, sell sheet, brand guidelines, document

**Generative-design** triggers on: generative art, algorithmic art, flow field, particle system, p5.js, data visualization, data viz, generative pattern, interactive chart

---

## Extending These Skills

### Adding a reference file

1. Create the `.md` file in the skill's `references/` folder
2. Add a line to the `## Files in This Skill` section of `SKILL.md`
3. Add a note in the skill body about when to read it

### Adding a sub-discipline

1. Add a row to the Sub-Disciplines table in `SKILL.md`
2. Add a `#### NEW SUB-DISCIPLINE` section under Step 3
3. Update the description frontmatter to include new trigger words

### Creating a 5th skill (e.g., motion-design, 3d-design)

Use the same 5-step workflow structure:
1. Identify sub-discipline
2. Define the aesthetic/system
3. Execute by sub-discipline (with specific craft notes)
4. Craft standards
5. Deliver (file + rationale + iteration note)

---

## Philosophy

These skills are designed around three principles:

**1. Domain knowledge is baked in.** The dashboard-patterns reference knows about
RevPAR and P&L coloring conventions. The print skill knows FP&A report structures.
The generative skill maps Recharts to trading data conventions. Generic creative skills
produce generic output — these are tuned to your context.

**2. Philosophy before execution.** Every skill requires establishing an aesthetic
direction before touching code or canvas. This prevents first-draft syndrome where
the output is technically correct but aesthetically empty.

**3. Craft standards are non-negotiable.** Every skill has explicit forbidden patterns
(no Inter+purple gradient, no default Word styles, no random color assignment).
Defining what's forbidden is as important as defining what to do.
