# Assetrail

Assetrail is a static, browser-based ledger viewer for ECO Systems real estate transactions. It loads an ECO Systems general ledger CSV, lets users filter and search property activity, and produces quick investor-friendly financial views without requiring a backend service.

## What it does

- Loads `ECO Systems General Ledger.csv` by default, or accepts a manually uploaded CSV.
- Filters transactions by property, category, date range, and text search.
- Shows transaction detail with running balances.
- Summarizes income, expenses, net balance, NOI, cap-rate context, and investment totals.
- Generates monthly income statement and balance sheet views.
- Supports CSV export and browser print/PDF output.
- Includes an investor view toggle for cleaner presentation.

## Project structure

```text
assetrail/
├── index.html                         # Single-page web app
├── ECO Systems General Ledger.csv      # Default ledger loaded by the app
├── favicon.svg
├── CNAME                              # Custom domain for static hosting
├── LICENSE
└── README.md
```

Historical `.bak.csv` and `.filtered.*.csv` files may appear during ledger refreshes. The live app expects the current default file to be named exactly:

```text
ECO Systems General Ledger.csv
```

## Running locally

Because the app fetches the CSV from the local project folder, serve it over HTTP instead of opening `index.html` directly:

```bash
cd /home/umbrel/Dropbox/Projects/assetrail
python3 -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

## Updating the ledger

1. Replace `ECO Systems General Ledger.csv` with the latest exported ledger.
2. Keep the filename unchanged unless you also update `defaultFilePath` in `index.html`.
3. Reload the page and use **Load Default** to verify the file parses correctly.
4. Commit/deploy the updated CSV with the app if publishing to static hosting.

## Deployment

Assetrail is a static site. Any static host can serve it as long as these files are available from the same directory:

- `index.html`
- `ECO Systems General Ledger.csv`
- `favicon.svg`
- `CNAME`, if using GitHub Pages/custom domain

No build step is required.

## Data caveats

- All financial views depend on the categories, property names, and dates present in the CSV.
- Browser-generated reports are lightweight operating views, not audited financial statements.
- If a CSV schema changes, update the parsing logic in `index.html` before relying on the output.

## Maintenance notes

- Keep large/generated backup files out of commits unless they are intentionally retained for audit history.
- Before publishing, confirm the CSV does not include private data that should not be exposed on a static website.
- After ledger refreshes, test filters, summary cards, income statement, balance sheet, CSV export, and print/PDF.
