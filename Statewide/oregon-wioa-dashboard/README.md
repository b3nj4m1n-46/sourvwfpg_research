# Oregon WIOA Workforce Data Dashboard — 2023 Extract

Data extracted from HECC's WIOA Title I Workforce Data Dashboard:
https://www.oregon.gov/highered/strategy-research/pages/dashboard-workforce.aspx

Underlying Power BI report: app.powerbigov.us (US Government cloud, "Publish to web" mode)

## Files

| File | Contents |
|------|----------|
| `participation-2023.csv` | Total participants & services + demographic breakdown (gender, age, race/ethnicity, barriers) |
| `workforce-boards-2023.csv` | Per-board participant totals (only statewide + Rogue captured) |
| `outcomes-2023.csv` | Measurable Skill Gains, Credential Attainment, Employment Rate 2Q After Exit |
| `earnings-2023.csv` | Median earnings 2 quarters after exit |
| `employment-4q-after-2023.csv` | Employment rate 4 quarters after exit (statewide + RV) |
| `earnings-4q-after-2023.csv` | Median earnings 4 quarters after exit (statewide only — RV column blank) |

## Filters applied

- **Program Year / Exit Year:** 2023
- **Program type:** All Programs (combined Adult, Dislocated Worker, Youth)
- **Workforce Board:** Two columns per file — `statewide` (all boards) and `rogue_workforce_partnership` (RV only)
- **Evaluation Period (Employment/Earnings):** 2 Quarters After Exit

## Conventions

- Empty cells = data suppressed in the dashboard (shown as `**`, typically when n is small enough to risk re-identification under HECC's Participant Protection Policy)
- Percentages stored as numeric (e.g. `47` means 47%, not 0.47)
- Dollar amounts rounded to nearest $500 by source (per Oregon Employment Department)

## Known gaps

See [GAPS.md](GAPS.md) for detailed capture instructions for each. Quick summary:

1. **RV 4Q earnings** — one missing cell in `earnings-4q-after-2023.csv`
2. **Per-program splits** — Adult / Dislocated Worker / Youth tabs not captured (combined "All Programs" only)
3. **Per-board breakdown** — only Statewide + Rogue captured; other 7 boards blank
4. **MSG Details (page 6)** — skill-gain type breakdown not captured
5. **Multi-year trends (page 3)** — observation only, no structured CSV

All gaps are documented with step-by-step capture instructions in [GAPS.md](GAPS.md).

## Source notes

- Earnings data from Oregon Employment Department, accurate as of 2/14/2025
- HECC notes that dashboard values may not match federal WIOA performance reports due to definition alignment changes
- Beginning PY 2023, Oregon changed eligibility determination, program enrollment, and service delivery procedures — affects year-over-year comparability
- Data source contact: hecc.rd@hecc.oregon.gov

## Extraction method

Power BI's "Publish to web" embed routes data through service workers that aren't captured by standard network tools. Data was extracted by:

1. Driving the Power BI viewer via browser automation (Claude in Chrome)
2. Setting filters page-by-page (slicers don't sync across pages in this report)
3. Screenshotting each visual and reading values via vision
4. Structured into the CSVs above

This means the values are accurate as displayed in the dashboard on 2026-05-23 but a fresh run of the dashboard at a later date could differ if HECC refreshes underlying data.
