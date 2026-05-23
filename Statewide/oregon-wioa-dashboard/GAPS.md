# Capture Gaps — Oregon WIOA Dashboard

Tracking what's NOT yet extracted from the HECC WIOA Title I Workforce Data Dashboard, so future captures can pick up where this left off.

**Dashboard URL:** https://www.oregon.gov/highered/strategy-research/pages/dashboard-workforce.aspx
**Direct Power BI URL** (skips the wrapper page):
`https://app.powerbigov.us/view?r=eyJrIjoiZTI3N2ZiM2YtZGRkOC00NGVlLWFmYWMtZmUxZDM1ZjE2MzJlIiwidCI6ImFhM2Y2OTMyLWZhN2MtNDdiNC1hMGNlLWE1OThjYWQxNjFjZiJ9&pageName=ReportSection39d11516e4275c002a2a`

---

## Gap 1 — RV 4Q After Earnings (one cell)

**What's missing:** The single `rogue_workforce_partnership_usd` column in [earnings-4q-after-2023.csv](earnings-4q-after-2023.csv).

**To capture:**
1. Open the Power BI view, navigate to page 9 (WIOA Earnings — Q2/4 After).
2. Set **Workforce Board** filter → only "Rogue Workforce Partnership".
3. Set **Evaluation Period** filter → "4 Quarters After".
4. Screenshot the page.
5. Fill the empty `rogue_workforce_partnership_usd` column in `earnings-4q-after-2023.csv` using the same row keys as `earnings-2023.csv`.

**Why it stalled:** Browser-automation clicks on the multi-select Workforce Board slicer kept landing on the wrong item — the items shift y-coordinate between renders, and clicks repeatedly hit Lane Workforce or Northwest Oregon instead of Rogue.

---

## Gap 2 — Per-program splits (Adult / Dislocated Worker / Youth)

**What's missing:** Every CSV currently uses the "All Programs" tab on each page, which is the combined total. The dashboard has Adult / Dislocated Worker / Youth tabs at the top of pages 2, 5, 6, 7, 8, 9.

**Scope estimate:** 3 programs × 5 data pages × 2 scopes (statewide + RV) = ~30 captures.

**To capture:**
1. For each page 2, 5, 7, 8, 9, click the "Adult" tab at the top, screenshot.
2. Repeat for "Dislocated Worker" and "Youth".
3. Repeat with Workforce Board = Rogue Workforce Partnership.
4. Add `program_type` column to each CSV (currently implicit "All Programs").

**Highest value first:** Page 2 (Participation) Adult & Dislocated Worker for both statewide & RV — that's 4 captures and probably covers the most asked questions.

---

## Gap 3 — Per-board breakdown

**What's missing:** [workforce-boards-2023.csv](workforce-boards-2023.csv) only has Statewide (8,134) and Rogue (1,230). The other 7 boards are blank.

**Boards still to capture:**
- Clackamas Workforce Partnership
- East Cascades Works
- Eastern Oregon Workforce Board
- Lane Workforce Partnership
- Northwest Oregon Works
- Southwestern Oregon Workforce Investment Board
- Willamette Workforce Partnership
- Worksystems

**To capture:**
1. On page 2, set Workforce Board filter to each board individually.
2. Read the Total Participants value.
3. Fill the corresponding row in `workforce-boards-2023.csv`.

**Scope estimate:** 8 captures (just totals). If you also want demographics per board, multiply by ~5x.

---

## Gap 4 — MSG Details (page 6)

**What's missing:** Skill-gain type breakdown — GED / Training Milestone / Skill Progress / Transcript / EFL Gain — across gender, age, race/ethnicity.

**To capture:**
1. Navigate to page 6 (MSG Details).
2. Screenshot statewide.
3. Set Workforce Board = Rogue, screenshot.
4. Output should be a new CSV like `msg-details-2023.csv` with columns `category` (gender/age/race), `subcategory` (Women, Men, etc.), `skill_gain_type` (GED, etc.), `percent_statewide`, `percent_rogue`.

**Scope estimate:** 2 captures, fairly heavy parse (5 skill-gain types × many demographic rows).

---

## Gap 5 — Multi-year participation trend

**What's missing:** Structured year-by-year participation counts. Currently only captured as a rough visual read from page 3:

| Year | Statewide Headcount (approx, from chart) |
|------|---|
| 2020 | ~8,800 |
| 2021 | ~9,800 |
| 2022 | ~11,100 |
| 2023 | ~8,100 |

3-year change: **-8%**

**To capture precisely:**
1. Navigate to page 3 (WIOA Participation Trends).
2. Hover over each data point in the line chart — Power BI shows the exact value in a tooltip.
3. Repeat for Rogue Workforce Partnership.
4. New CSV `participation-trend.csv` with columns `year`, `statewide_headcount`, `rogue_headcount`.

**Bonus:** Page 3 has left-side tabs for Race/Ethnicity, Gender, Barriers — same trend chart broken out by demographic. Worth capturing if year-over-year demographic shift matters.

---

## Recommended order if revisiting

1. **Gap 1** — smallest fix, completes a single cell.
2. **Gap 5** — small data, useful context.
3. **Gap 3 totals only** — 8 captures, useful regional context.
4. **Gap 4** — 2 captures, niche detail.
5. **Gap 2** — largest, do only if a specific program type is asked.

## Easier path: human-in-the-loop

For all gaps, the fastest path is: you drive the dashboard, take screenshots, drop them into a folder, and Claude parses to CSV. Browser automation works for navigation but the multi-select Workforce Board slicer is unreliable enough that each click costs several attempts.
