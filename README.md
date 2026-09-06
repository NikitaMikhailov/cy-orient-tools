# 🗺️ cy-orient-tools

**Registration table → IOF XML 3.0 converter for orienteering events.**

A single-page, zero-dependency tool that turns an Excel registration table into a valid [IOF XML 3.0](https://www.orienteering.org/resources/it/data-standard-3-0/) `CompetitorList`, ready to import into **SPORTident Center**. Built for Cyprus Orienteering event organisers.

[![Deploy to GitHub Pages](https://github.com/NikitaMikhailov/cy-orient-tools/actions/workflows/deploy.yml/badge.svg)](https://github.com/NikitaMikhailov/cy-orient-tools/actions/workflows/deploy.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**🔗 Live tool:** https://nikitamikhailov.github.io/cy-orient-tools/

---

## What it does

Race organisers keep entries in an Excel sheet. SPORTident Center needs an IOF XML 3.0 competitor list. This tool bridges the two with a simple copy → paste → review → download flow, entirely in the browser — no data is uploaded anywhere.

1. **Paste** — copy the full registration table from Excel (`Ctrl+A`, `Ctrl+C`) and paste it in.
2. **Review** — the tool parses rows, assigns per-course IDs (`A-001`, `B-002`, …), and flags problems.
3. **Download** — export a ready-to-import IOF XML 3.0 file, or copy it straight to the clipboard.

## Features

- 📋 Paste directly from Excel — no CSV export needed
- 🏷️ Auto-generates course-based competitor IDs
- ⚠️ Validates data as you go: missing SI card, duplicate SI cards, missing birth year, ambiguous name splits
- ✏️ Editable review table — fix any field before exporting
- 📄 Produces a spec-compliant IOF XML 3.0 `CompetitorList`
- 🔒 100% client-side — nothing leaves your browser
- ⚡ No build step, no dependencies — one HTML file

## Usage

Open the [live tool](https://nikitamikhailov.github.io/cy-orient-tools/), or run it locally:

```bash
git clone https://github.com/NikitaMikhailov/cy-orient-tools.git
cd cy-orient-tools
python3 -m http.server 8000
# open http://localhost:8000
```

Then:

1. Select and copy your registration table in Excel (including the header row).
2. Paste it into the text area and click **Parse**.
3. Review the parsed rows — warnings are highlighted in orange.
4. Fix any flagged fields directly in the table.
5. Click **Download IOF XML 3.0** (or **Copy XML**) and import the file into SPORTident Center.

### Expected table columns

| FULL NAME | OUR SI CARD | OWN SI CARD | AGE | YEAR | Club | COURSE |
|---|---|---|---|---|---|---|

## Tech stack

Plain HTML, CSS, and JavaScript — no framework, no build tooling. Deployed automatically to GitHub Pages on every push to `main` via [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml).

## Contributing

Issues and pull requests are welcome. Since this is a single static file, most changes can be tested by simply opening `index.html` in a browser.

## License

[MIT](LICENSE)
