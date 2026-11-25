# 🌿 Urban Air Quality Assistant

An accessible, offline-first web app that turns an Air Quality Index (AQI) reading into a clear category, personalised health advice, a trend chart, and exportable history.

**Live demo:** `https://<your-github-username>.github.io/airquality-assistant/`
**Author:** Gundluru Rajasekhar

## Problem
City residents see AQI numbers every day but rarely know what they mean for their health. Children, older adults, and people with asthma or heart conditions need immediate, specific guidance, not technical reports.

## Solution
Enter an AQI (0-500), pick who the advice is for, and get the category, a risk score, an alert for dangerous levels, and tailored actions. Every check is saved locally so you can see trends, compare places, and export your data.

## Features
- Six-level US EPA AQI classification with colour, text label, gauge, and 0-100 risk score
- Input validation with accessible error messages (whole numbers 0-500 only)
- Advice tailored to general public, children, elderly, respiratory/heart conditions, outdoor workers
- Health alert (AQI 201+) and emergency pollution alert (AQI 301+)
- Voice guidance: "Read aloud" speaks the result (browser Speech Synthesis)
- Trend chart (dependency-free SVG), statistics (count, average, highest, lowest)
- Multi-place comparison table (latest reading per place)
- Export history as CSV (formula-injection safe) and download a text report
- Light/dark theme toggle (remembers choice, follows system default)
- Built-in automated self-tests (20 checks) runnable from the page
- Works offline, no API keys, no tracking

## Screenshots
Add your screenshots to the repository and reference them here:
```
![Checker](screenshots/checker.png)
![Trend and history](screenshots/trend.png)
![Self-tests](screenshots/tests.png)
```

## Architecture
Single `index.html` with six separated JavaScript modules (plain objects, no globals beyond the module names):

| Module | Responsibility |
|--------|----------------|
| `AQI` | Pure logic: levels, validation, advice, risk score (no DOM, fully testable) |
| `Store` | localStorage with safe fallback, CSV export, statistics, per-place grouping |
| `A11y` | Error announcement, focus handling, theme, voice |
| `Charts` | SVG trend chart |
| `UI` | Rendering and event wiring (uses `textContent` only) |
| `Tests` | In-browser automated test runner for the logic modules |

Data flow: input → `AQI.validate` → `AQI.levelIndex`/`advise` → render → `Store.add` → history, chart, comparison.

## Installation
1. Download or clone the repository.
2. Open `index.html` in any modern browser. No build step.

**Deploy to GitHub Pages:** Settings → Pages → Source: `main` branch, `/ (root)` → Save.

## Test Cases
Open the page and press **Run self-tests**. Core cases:

| Input | Expected |
|-------|----------|
| AQI 25 | Good |
| AQI 75 | Moderate |
| AQI 125 | Unhealthy for Sensitive Groups |
| AQI 175 | Unhealthy |
| AQI 250 | Very Unhealthy |
| AQI 400 | Hazardous |
| 0, 50, 51, 500 | Boundaries: Good, Good, Moderate, Hazardous |
| blank, -5, 600, 12.5, abc | Rejected with an error |
| Children at AQI 135 | Child-specific tip added |
| `=SUM(1)` in CSV | Exported as `'=SUM(1)` (safe) |

## Accessibility
Skip link, semantic landmarks, labelled inputs with `aria-describedby`, `role="alert"` errors, live-region results, `role="meter"` risk score, text labels in addition to colour, visible focus, full keyboard use, dark mode, reduced-motion support, responsive down to 320px.

## Security and Privacy
`textContent` only (no `innerHTML`), range and length limits, CSV formula neutralisation, no third-party scripts, no network requests. Data stays in your browser and can be cleared at any time.

## Future Scope
Live AQI from public APIs, city search and maps, forecasts from real data, multilingual support (Telugu, Hindi, English), installable PWA with service worker, push alerts.

## Changelog
- **v2:** modular JS, self-tests, trend chart, comparison, CSV/report export, alerts, voice, theme toggle, expanded docs
- **v1:** AQI checker with six categories, advice, and history

## Disclaimer
General information, not medical advice.

## License
MIT. Add a `LICENSE` file to the repository root for full effect.
