# 10-K Analyzer by Alexander

Each company's latest annual report (10-K / 20-F / 40-F) as an infographic, slides with voice-over, an animated video and a written report.

- `index.html` — the site (layout and code only)
- `data/index.json` — list of companies for search
- `data/companies/TICKER.json` — one file per company, loaded when opened
- `vendor/html-to-image.js` — draws the downloadable infographic PNG in the browser (MIT licence)
- Maintenance scripts live in a separate private repository.

The site is static. Pushing to `main` redeploys it to GitHub Pages through `.github/workflows/pages.yml`
(Settings → Pages → Source: GitHub Actions). Figures come from company filings with the SEC and StockAnalysis; see each company's footnotes.
