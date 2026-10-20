# Statistical Data Visualization v1.0 — Test Report & Product Listing

**File:** `index.html` (98.9 KB — limit 150 KB) · single file, all CSS/JS inline, zero external assets, zero network calls, no localStorage, no service workers, no permissions, no parent-window access. Safe for the sandboxed Wix iframe. It shares its statistics engine with Statistical Data Analysis v1.0 (verified 41/41 against scipy) and leads with visualization.

## What it does
- **Data in:** CSV, **XLSX** (a real reader written into the page — ZIP unpacking + worksheet XML parsing; first worksheet used), **DAT** (whitespace/tab-delimited text), TSV, TXT, JSON, paste, or the built-in sample. Delimiter auto-detection, quoted fields, thousands separators, decimal commas, missing-value tokens. Legacy binary **.xls** is detected and refused with guidance (Save As → XLSX or CSV) — honest, not faked. XLSX unpacking uses the browser's built-in decompression (current Chrome/Edge/Firefox/Safari); older browsers get the same clear guidance.
- **Visualize tab (the headline):** Distribution plot (histogram + KDE density curve + mean line, adjustable bins) · Box plots (single or grouped) · Scatter with fitted line and r · Line chart in row order · Pie chart of composition (top 9 + "Other") · Normal Q–Q plot for the normality check · Correlation heatmap (colour-coded matrix) · PCA biplot (observation dots + variable arrows). Every chart can be downloaded as a PNG.
- **Analysis tabs:** the full toolkit — Descriptive, T-Tests (one-sample / Welch / pooled / paired), ANOVA, Chi-Square, Correlation, Regression, Multiple Regression (collinearity detection), PCA, Factor Analysis (PAF + varimax) — with APA-style tables, plain-language interpretations and a downloadable HTML report.

## Product listing (for the Asif SaaS Studio CMS — `SaasProducts`)
- **Name:** Statistical Data Visualization — Charts, Graphs & Analysis
- **Slug:** `statistical-data-visualization`
- **Category:** Productivity
- **Version:** 1.0
- **Summary:** See your data: upload CSV, XLSX or DAT and get distribution plots, box plots, scatter plots, heatmaps, Q–Q plots and PCA biplots — plus full statistical analysis with tables and plain-language interpretations. Everything runs locally; nothing is uploaded.
- **appHtml:** upload `index.html` (this file)
- **Demo:** Yes · **Published:** Yes

## Verification
- **XLSX end-to-end (10 checks):** a real workbook generated with Excel's library (openpyxl) — headers, shared-string text (incl. a Unicode name), numeric cells, an empty cell, and a second sheet — parsed correctly into a typed dataset: strings resolved, Score numeric, Group categorical, empty cell treated as missing, column mean exact, second sheet ignored as designed.
- **DAT & text routing (4 checks):** whitespace-delimited DAT parses into numeric columns; CSV and semicolon files still route correctly through the same smart loader.
- **New mathematics (5 checks):** inverse-normal values match the reference (Φ⁻¹(0.975) = 1.960, Φ⁻¹(0.001) = −3.090); the KDE density curve integrates to 1.00 and is finite/non-negative everywhere.
- **Inherited engine:** the statistics core is byte-identical to the one verified 41/41 against scipy in the sibling product; spot-rechecked here (Welch t = −6.400 vs scipy −6.4).
- **A build bug caught by structural checks:** the first assembly inserted the visualization script at the first `</body>` string in the file — which lives inside the report-generator's JavaScript — corrupting the page structure. The syntax/structure audit caught it before any testing; the assembly was redone anchored at the document end and re-verified (4 clean script blocks, full syntax pass, 98.9 KB).

## Manual testing checklist
- [ ] Open `index.html` in Chrome/Edge — loads cleanly, Visualize tab selected by default
- [ ] Load the sample dataset → Distribution of PostTest shows histogram + red density curve; move the bins slider
- [ ] Box plot of PostTest grouped by Group; Pie of Group; Line of StudyHours
- [ ] Scatter StudyHours × PostTest → fitted line + r in the interpretation
- [ ] Q–Q plot of PostTest → points near the line
- [ ] Correlation heatmap (all numeric) and PCA biplot → arrows + dots render; Download chart (PNG) works
- [ ] Upload a real .xlsx from Excel → first sheet loads with correct types; upload a legacy .xls → friendly refusal
- [ ] Upload a whitespace .dat file → loads as numeric columns
- [ ] Run one analysis per remaining tab (t-test, ANOVA, regression, PCA, FA) → tables + interpretations
- [ ] Download report → formatted HTML with charts embedded
- [ ] Resize to ~380 px → layout stacks; tables scroll
- [ ] After CMS upload, open `app.html?slug=statistical-data-visualization` → run the sample end-to-end in the iframe
