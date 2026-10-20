# Statistical Data Visualization — Charts, Graphs & Analysis

See your data before you test it: a visualization-first statistics workbench in a single web page — **100% in your browser**. No uploads, no sign-up, no server.

**▶ Live on Asif SaaS Studio:** open the tools catalogue and choose *Statistical Data Visualization* (slug `statistical-data-visualization`).

## What it does
1. **Load data** — CSV, **XLSX** (a real workbook reader written into the page; first worksheet), **DAT** (whitespace-delimited), TSV, TXT, JSON, paste, or the built-in sample dataset. Legacy binary .xls is detected and refused with guidance.
2. **Visualize** — a Visualize tab with 8 chart types: distribution (histogram + density curve), box plots (single or grouped), scatter with fitted line, line chart, pie, normal Q–Q plot, correlation heatmap, PCA biplot. Every chart downloads as PNG.
3. **Analyse** — the full toolkit of its sibling *Statistical Data Analysis*: descriptives, t-tests, ANOVA, chi-square, correlation, regression, multiple regression, PCA and factor analysis, each with a table and a plain-language interpretation.
4. **Report** — download a formatted HTML report.

## Use
Open `index.html` in any modern browser — or from this repo via any static host. No build step, no dependencies.

- Single file, **98.9 KB**, all CSS/JavaScript inline
- No localStorage, no service workers, no browser permissions, no parent-window access — safe in a sandboxed iframe
- Responsive layout in the Asif SaaS Studio emerald + lime branding

## Testing
The statistics engine is shared with Statistical Data Analysis and verified **41/41 against scipy**; the visualization and format additions passed 20/21 checks including an end-to-end read of a real openpyxl-generated workbook (the one failure was a wrong constant in the test itself — the engine matched scipy). Full report: `statistical-data-visualization-test-report.md`. Complete documentation: `docs/statistical-data-visualization-docs.pdf`.

Created by Dr. Asif Ahmad · Asif SaaS Studio · v1.0
