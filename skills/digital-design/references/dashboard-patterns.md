# Dashboard Layout Patterns & Data Conventions

Reference for building data-dense interfaces. Optimized for FP&A, trading,
and hospitality operations contexts.

---

## Layout Hierarchy (always in this order top-to-bottom)

```
1. GLOBAL CONTROLS        — Date range, filters, entity selector (top bar)
2. KPI SUMMARY STRIP      — 4–6 headline numbers, always above the fold
3. PRIMARY VISUALIZATION  — The chart that answers the main question
4. SECONDARY CHARTS       — Supporting context (2–3 smaller charts)
5. DETAIL TABLE           — Full data, sortable, with search
```

Never bury the headline number. The most important KPI is always visible without scrolling.

---

## KPI Card Pattern

```
┌─────────────────────┐
│ LABEL (10px, mono)  │
│ $1,234,567          │  ← Primary value: largest type on the page
│ ▲ +12.4%  vs LY    │  ← Delta: colored (green/red), with comparison label
│ ████████░░  78%     │  ← Optional: sparkline or progress bar
└─────────────────────┘
```

- Label: uppercase, monospaced, 10–11px, muted color
- Primary value: 28–40px, monospaced, full text color
- Delta: 12–13px, semantic color (positive/negative), include comparison period
- Never use a KPI card without a delta — a number without context is useless

---

## Chart Type Decision Tree

| Question | Best chart |
|---|---|
| How is X trending over time? | Line chart |
| How do categories compare? | Horizontal bar (never vertical for many categories) |
| What's the composition of X? | Stacked bar or area (NOT pie charts) |
| Where does X rank vs peers? | Sorted horizontal bar |
| How do two variables relate? | Scatter plot |
| What's the distribution? | Histogram or box plot |

**Never use pie charts for more than 2 segments.** Always label data directly on the chart — no legends that force the eye to travel.

---

## Color Conventions (Semantic, Not Decorative)

```
Positive / favorable:   #4ade80  (green)
Negative / unfavorable: #f87171  (red)
Neutral / baseline:     #60a5fa  (blue)
Warning / watch:        #fbbf24  (amber)
Inactive / historical:  rgba(255,255,255,0.2)
```

Use color to signal meaning, not to decorate. A chart with 6 different colors is a chart that communicates nothing.

---

## Number Formatting Conventions

| Value type | Format | Example |
|---|---|---|
| Currency large | $X.XM or $X.XB | $4.2M |
| Currency exact | $X,XXX,XXX | $4,200,000 |
| Percentage | XX.X% | 12.4% |
| Basis points | XXbps | 125bps |
| Index / ratio | X.XX | 1.23 |
| Count | X,XXX | 4,200 |

Always right-align numbers in tables. Left-align text. Never center-align numbers.
Use monospaced font for all numeric data.

---

## Trading-Specific Patterns

For P&L and trading interfaces:
- Green for positive P&L / long positions
- Red for negative P&L / short positions underwater
- Show position size, entry, current, P&L ($), P&L (%) — in that order
- Sparklines should show the full session, not just recent movement
- Mark entry price on sparklines as a horizontal reference line

---

## Hospitality Operations Patterns

For RevPAR / occupancy dashboards:
- Primary KPIs: Occupancy %, ADR, RevPAR — always the top three
- Compare current period vs: Budget, Prior Year, Competitive Set
- Color code: above budget = green, below = red, within 2% = neutral
- STR data if available: show market index (MPI, ARI, RGI)
- Pace reports: show pickup curve, booking window distribution

---

## Table Conventions

- Sortable columns: all numeric columns sortable by default
- Zebra striping: very subtle (2–3% opacity difference)
- Sticky header: always for tables > 10 rows
- Row hover: highlight entire row, not just cell
- Action column: always rightmost
- Pagination: show "X–Y of Z" and rows-per-page selector
