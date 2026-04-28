---
name: generative-design
description: >
  Create algorithmic art, generative visual systems, interactive data visualizations,
  and code-driven design. Use this skill whenever the user wants something produced
  by a system or algorithm rather than drawn by hand — flow fields, particle systems,
  noise-based art, generative brand patterns, data art, or any creative output where
  code is the medium. Trigger on: "generative art", "algorithmic art", "flow field",
  "particle system", "create with p5.js", "visualize my data as art", "build a
  generative pattern", "data visualization", "make an interactive chart", "create a
  visual from this data", or any request where randomness, rules, and code are the
  creative tools. Also trigger when the user wants to turn a dataset into a visual
  narrative or build a reusable visual system that produces unique outputs each time.
---

# Generative Design Skill

This skill governs code-driven, algorithmic, and data-visual creative output.
The designer authors a system; the system produces the work. Every output is
unique, reproducible via seed, and capable of infinite variation.

## Sub-Disciplines

| Sub-Discipline | Triggers | Primary Output |
|---|---|---|
| Algorithmic Art | "flow field", "particle", "noise art", "generative piece" | HTML + p5.js |
| Data Visualization | "chart", "viz", "visualize this data", "dashboard chart" | React + Recharts/D3 |
| Generative Patterns | "pattern", "texture", "generative brand system" | HTML/SVG |
| AI-Assisted Concept | "explore styles", "generate variations", "rapid concepts" | Image prompts + brief |

---

## Workflow

### Step 1 — Identify Sub-Discipline & Extract Intent

Parse the request for:
- **Input**: Is there data to visualize? A concept to express? A mood or theme?
- **Interactivity**: Should the output respond to user input? Have controls?
- **Reproducibility**: Does it need a seed for consistent re-generation?
- **Scale**: Single artwork? Repeating system? Series of variations?
- **Aesthetic intent**: Scientific/precise? Organic/flowing? Bold/graphic?

### Step 2 — Define the Generative System

Before writing code, define the rules of the system:

```
Algorithm:     [What mathematical/computational process drives this?]
Parameters:    [What can vary? What is fixed?]
Seed control:  [How is randomness controlled for reproducibility?]
Color logic:   [How are colors assigned — by value, velocity, position, noise?]
Termination:   [When does the system stop / reach equilibrium?]
```

For algorithmic art: also write an **Algorithmic Philosophy** (2–3 sentences naming
the movement and its computational aesthetic). See `references/generative-philosophy.md`.

### Step 3 — Execute by Sub-Discipline

#### ALGORITHMIC ART (p5.js)
- Use the algorithmic-art skill approach: philosophy → code → interactive HTML.
- Always implement seeded randomness (`randomSeed(seed)` in p5.js).
- Provide a seed input or slider so the user can explore variations.
- Color mapping: tie color to a meaningful variable (velocity, density, time, noise value).
- Performance: test at 60fps for particle systems; cap particle count if needed.
- Export as standalone HTML file with embedded p5.js.

**Standard p5.js structure:**
```javascript
// Always use this pattern
let seed = 42;
function setup() {
  createCanvas(windowWidth, windowHeight);
  randomSeed(seed);
  noiseSeed(seed);
  background(bg);
}
function draw() {
  // system update loop
}
```

See `references/p5-patterns.md` for ready-to-use algorithmic patterns.

#### DATA VISUALIZATION
- Read the user's data first — understand its shape before choosing a chart type.
- Apply the chart decision tree from `references/viz-decision-guide.md`.
- Use Recharts for React output. Use D3 for custom/complex visualizations.
- Color: semantic (positive/negative) OR categorical (max 7 distinct colors) — never decorative.
- Always label data directly. Never rely on a distant legend.
- Provide interactivity: hover tooltips minimum, click-to-filter when useful.
- For trading data: P&L color conventions (green/red), monospaced numbers, sparklines.
- For hospitality data: RevPAR/ADR/Occ hierarchy, comp set benchmarking.

**Recharts boilerplate:**
```jsx
import { LineChart, Line, XAxis, YAxis, Tooltip, ResponsiveContainer } from 'recharts';
// Always wrap in ResponsiveContainer for responsive behavior
```

#### GENERATIVE PATTERNS
- Define the tile unit first, then the repeat logic.
- Three pattern types: Grid (regular), Phyllotaxis (organic/spiral), Noise-displaced (flowing).
- Provide color palette as CSS custom properties so the user can retheme.
- Export as SVG for scalability, or HTML with canvas for animation.
- For brand applications: ensure the pattern works at 3 scales (thumbnail, full-bleed, detail).

**Pattern quality check:**
- Does it tile seamlessly? (For repeating patterns)
- Does it read at multiple scales?
- Is the color palette intentional, not random?
- Can the user adjust density, scale, and color easily?

#### AI-ASSISTED CONCEPT EXPLORATION
- When the user wants rapid visual concepts without code output:
- Generate 3–5 detailed image-generation prompts (for Midjourney, Firefly, or DALL-E).
- Each prompt should specify: subject, style, composition, color palette, lighting, mood.
- Also generate a brief: what each direction explores and how they differ strategically.
- Format: numbered list of prompts + 2-sentence rationale per prompt.

**Prompt structure:**
```
[Subject description], [style/aesthetic reference], [composition note],
[color palette], [lighting], [quality modifiers: high detail, etc.]
```

### Step 4 — Craft Standards for Generative Work

- **Intentional randomness**: Random doesn't mean arbitrary. Every parameter's range
  is tuned for aesthetic quality. Bad generative art has parameters that are too wide.
- **Mathematical beauty**: Favor natural constants (golden ratio, Fibonacci, primes)
  as organizing principles. They produce inherently pleasing emergent patterns.
- **Color discipline**: Use a maximum of 5–6 colors. Map them to meaningful variables.
  Never assign colors randomly — map them to data or computational state.
- **Performance matters**: Art that runs at 15fps is bad art. Optimize.
- **Seed everything**: Any randomness must be seedable. A piece the user loves
  must be reproducible.

### Step 5 — Deliver

1. The working code file (HTML with embedded JS, or JSX component)
2. A plain-English explanation of how the system works (the algorithm, not the code)
3. A list of the 3 most interesting parameters to adjust and what they control
4. The seed used (if applicable), so the exact output can be reproduced

---

## Quick Reference: Algorithms by Aesthetic

| Desired look | Algorithm |
|---|---|
| Flowing, organic | Perlin noise flow field |
| Crystalline, geometric | Voronoi tessellation |
| Dense, textural | Reaction-diffusion (Gray-Scott) |
| Spiral, natural | Phyllotaxis / Fibonacci spiral |
| Chaotic, energetic | Lorenz attractor |
| Structural, architectural | L-systems / fractal branching |
| Ethereal, gaseous | Layered simplex noise with alpha |
| Sharp, data-driven | Force-directed graph |

---

## Files in This Skill

- `references/generative-philosophy.md` — Named algorithmic aesthetic movements
- `references/p5-patterns.md` — Ready-to-use p5.js pattern templates
- `references/viz-decision-guide.md` — Chart type selection by data shape and question
- `references/image-gen-prompts.md` — Prompt templates for AI image generation tools
