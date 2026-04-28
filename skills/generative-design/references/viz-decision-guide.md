# Visualization Decision Guide

Choosing the right chart type based on the question being asked and the data shape.

---

## The Decision Tree

### What kind of question is this?

**Trend over time?**
→ Line chart (continuous data) or Bar chart (discrete periods)
→ Use area chart only if showing cumulative or part-of-whole over time
→ Never: Pie chart for time series

**Comparison between categories?**
→ Horizontal bar chart (best for many categories, long labels)
→ Grouped bar chart (if comparing 2–3 metrics per category)
→ Never: Pie chart for more than 2 categories

**Distribution / spread?**
→ Histogram (for continuous data, many values)
→ Box plot (for showing quartiles, outliers)
→ Violin plot (for distribution shape detail)
→ Never: Bar chart for distributions

**Relationship between two variables?**
→ Scatter plot
→ Bubble chart (if adding a 3rd quantitative dimension)
→ Never: Line chart (implies temporal connection that may not exist)

**Part of a whole?**
→ Stacked bar (best for showing composition over time or categories)
→ Treemap (best for hierarchical part-of-whole with many items)
→ Pie chart ONLY for exactly 2 categories (e.g., pass/fail, yes/no)

**Ranking?**
→ Sorted horizontal bar chart (always sorted, highest to lowest)
→ Bump chart (for rank change over time)

**Geographic data?**
→ Choropleth map (region shading by value)
→ Dot map (for point locations with magnitude)

---

## Chart Sizing & Layout

| Chart type | Min width | Ideal aspect ratio |
|---|---|---|
| Line chart | 400px | 16:9 |
| Bar chart (horizontal) | 400px | 3:4 |
| Bar chart (vertical) | 300px | 4:3 |
| Scatter plot | 400px | 1:1 |
| KPI sparkline | 80px | 3:1 |
| Treemap | 500px | 16:9 |

---

## Recharts Component Map

| Chart type | Recharts component |
|---|---|
| Line | `<LineChart>` + `<Line>` |
| Bar (vertical) | `<BarChart>` + `<Bar>` |
| Bar (horizontal) | `<BarChart layout="vertical">` + `<Bar>` |
| Area | `<AreaChart>` + `<Area>` |
| Scatter | `<ScatterChart>` + `<Scatter>` |
| Composed (mixed) | `<ComposedChart>` + multiple series |
| Sparkline | `<LineChart>` no axes, minimal padding |
| Radial | `<RadialBarChart>` |

Always wrap in `<ResponsiveContainer width="100%" height={height}>`.

---

## Domain-Specific Conventions

### Trading / Portfolio Data
- P&L: Line or Area chart with fill below zero in red, above zero in green
- Sparklines: Always show with price reference line at entry or zero
- Drawdown: Area chart filled red, absolute values, duration on x-axis
- Position table: Columns in order: Symbol | Side | Size | Entry | Current | P&L$ | P&L%

### FP&A / Financial Reporting
- Revenue vs Budget: Grouped bar — actual (solid), budget (hatched or lighter)
- Variance: Waterfall chart (start → drivers → end)
- Margin trend: Dual-axis line (revenue bar + margin % line)
- Rolling periods: Use 'TTM' or 'LTM' labels, not just "12 months"

### Hospitality / RevPAR
- Occupancy, ADR, RevPAR: Always in this order, always as 3 KPI cards minimum
- Comp set: Show as small multiples or overlay on same chart
- Pace: Plot bookings-on-hand vs. same-day-last-year, by arrival date
- STR indices: MPI, ARI, RGI — benchmark to 100 (above = gaining share)

---

## Axis & Label Best Practices

- X-axis labels: Date formats — "Jan" for months, "Q1 '25" for quarters, "FY25" for years
- Y-axis: No more than 5–6 tick marks. Always include zero unless range is very tight.
- Data labels: Direct labeling on data > legend when < 5 series
- Tooltips: Always include: label, value, formatted number, unit, comparison period
- Grid lines: Horizontal only. Very light (5–8% opacity on dark, 8–12% on light).
