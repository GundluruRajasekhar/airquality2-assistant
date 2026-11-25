# Tasks: Urban Air Quality Assistant (v2)

Legend: ✅ done · ⬜ to do

## Phase 1: Planning
- ✅ T1. Review v1 and evaluation feedback (score 86.41)
- ✅ T2. Identify gaps: modularity, testing, visual data, export, documentation
- ✅ T3. Keep the four-file format (index.html, requirements.md, readme.md, tasks.md)

## Phase 2: Architecture
- ✅ T4. Split logic into modules: `AQI`, `Store`, `A11y`, `Charts`, `UI`, `Tests`
- ✅ T5. Keep `AQI` pure (no DOM) so it can be tested directly

## Phase 3: Build
- ✅ T6. Validation with accessible errors (whole numbers 0-500)
- ✅ T7. Six-level classification, gauge, and 0-100 risk score
- ✅ T8. Audience-specific advice
- ✅ T9. Health alert (201+) and emergency alert (301+)
- ✅ T10. History (last 20), statistics, and SVG trend chart
- ✅ T11. Place comparison table
- ✅ T12. CSV export (formula-safe) and text report download
- ✅ T13. Voice guidance (Read aloud)
- ✅ T14. Light/dark theme toggle with saved choice
- ✅ T15. Built-in automated self-tests (20 checks)

## Phase 4: Quality
- ✅ T16. Accessibility: labels, `aria-describedby`, `role="alert"`, `role="meter"`, live regions, skip link, focus, reduced motion
- ✅ T17. Security: `textContent` only, input limits, CSV neutralisation, no external calls
- ✅ T18. Responsive pass (320px to desktop)
- ✅ T19. README with Problem, Solution, Features, Screenshots, Architecture, Installation, Test Cases, Accessibility, Security, Future Scope, Changelog

## Phase 5: Manual Test Checklist
| # | Action | Expected |
|---|--------|----------|
| 1 | Click Run self-tests | "20 of 20 tests passed" |
| 2 | AQI 135 + Children | Sensitive Groups, child tip first |
| 3 | AQI 340 | Emergency alert banner, Hazardous |
| 4 | AQI 245 | Health alert banner |
| 5 | Blank, -5, 600, 12.5 | Error shown, focus returns to field |
| 6 | Three checks | Trend chart and statistics appear |
| 7 | Two different places | Comparison table appears |
| 8 | Export CSV | File downloads with header and rows |
| 9 | Read aloud | Result is spoken (or a clear unsupported message) |
| 10 | Theme button | Switches light/dark; choice persists after reload |
| 11 | Tab key only | All controls reachable with visible focus |
| 12 | Phone width (320px) | No sideways page scroll |
| 13 | Clear history | Chart, table, and comparison hidden |

## Phase 6: Release
- ⬜ T20. Replace the four files in the repository with the v2 files
- ⬜ T21. Add screenshots to a `screenshots/` folder and check the links in `readme.md`
- ⬜ T22. Add `LICENSE` (MIT) to the repository root
- ⬜ T23. Open the live link and run the checklist above
- ⬜ T24. Resubmit the live link

## Phase 7: Future Scope
- ⬜ Installable PWA (manifest and service worker)
- ⬜ Live AQI from public APIs and city search
- ⬜ Forecasts based on real data
- ⬜ Multilingual support (Telugu, Hindi, English)
