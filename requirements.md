# Requirements: Urban Air Quality Assistant (v2)

## 1. Problem Statement
Residents see AQI numbers without knowing what they mean for their health. They need a fast, trustworthy way to turn a reading into a category and practical actions, especially children, older adults, and people with respiratory or heart conditions.

## 2. Goals
- Classify any AQI (0-500) instantly using the standard EPA scale.
- Give audience-specific advice and alerts for dangerous levels.
- Let users track, compare, and export readings.
- Work offline, privately, and accessibly on any device.

## 3. Users
Citizens, parents, older adults, patients, outdoor workers and athletes.

## 4. Functional Requirements
| ID | Requirement | Priority |
|----|-------------|----------|
| FR-1 | Enter AQI; whole numbers 0-500 only, with clear error message | Must |
| FR-2 | Show category, description, colour, gauge, and 0-100 risk score | Must |
| FR-3 | Advice per category plus extra tip for selected audience | Must |
| FR-4 | Health alert at AQI 201+, emergency alert at 301+ | Must |
| FR-5 | Save last 20 checks locally; table, statistics, and SVG trend chart | Must |
| FR-6 | Compare latest reading across places | Should |
| FR-7 | Export history as CSV; download text report | Should |
| FR-8 | Voice guidance via "Read aloud" | Should |
| FR-9 | Light/dark theme toggle with saved choice | Should |
| FR-10 | Built-in self-tests for logic, validation, and CSV safety | Must |
| FR-11 | AQI scale reference, tips, About, and disclaimer | Should |

## 5. Non-Functional Requirements
| Area | Requirement |
|------|-------------|
| Code quality | Separate modules (`AQI`, `Store`, `A11y`, `Charts`, `UI`, `Tests`); pure logic has no DOM access; strict mode; commented functions |
| Accessibility | Labels, `aria-describedby`, `role="alert"`, live regions, `role="meter"`, skip link, visible focus, keyboard-only use, text labels with colour, reduced motion |
| Responsiveness | 320px to desktop; tables scroll inside containers |
| Performance | Single file, no libraries, no network requests |
| Security | `textContent` only; input limits; CSV formula neutralisation; no third-party scripts |
| Privacy | All data local; clearable |
| Reliability | Works if localStorage is blocked or speech is unsupported |
| Compatibility | Current Chrome, Edge, Firefox, Safari |

## 6. AQI Categories
0-50 Good · 51-100 Moderate · 101-150 Unhealthy for Sensitive Groups · 151-200 Unhealthy · 201-300 Very Unhealthy · 301-500 Hazardous

## 7. Acceptance Criteria
1. AQI 25, 75, 125, 175, 250, 400 give Good, Moderate, Sensitive Groups, Unhealthy, Very Unhealthy, Hazardous.
2. Blank, -5, 600, 12.5, and text are rejected with an error and no result.
3. Selecting Children at AQI 135 adds a child-specific tip; at AQI 40 it does not.
4. AQI 340 shows the emergency alert; AQI 245 shows the health alert.
5. Three or more checks draw a trend chart; two places show a comparison table.
6. CSV export neutralises cells beginning with `=`, `+`, `-`, or `@`.
7. "Run self-tests" reports all 20 tests passed.
8. Everything is usable with keyboard only; no console errors; no network requests.

## 8. Constraints and Out of Scope
AQI is entered manually. No live data feeds, forecasts, accounts, or PWA service worker in this version (listed under Future Scope). Advice is general, not medical.
