# Decks

Presentation source files for the SOURVWF research.

## Active deck

**`sou_workforce_pell`** — proposal that SOU adopt a Workforce Pell track under the brand "Applied Bioregional Learning." Audience: SOU administration + Rogue Valley community + (secondary asks to) HECC + WTDB + the Governor's Office.

| File | Role |
|------|------|
| `sou_workforce_pell.html` | **Source of truth.** Edit here first. Built with React/Babel + custom CSS, designed for projection at 1920×1080. |
| `sou_workforce_pell.tex` | Beamer mirror, kept in sync for printable/handout output. xelatex required. |
| `sou_workforce_pell.pdf` | Latest rendered PDF (from the tex). Committed so partners can preview without compiling. |

19 slides:

| # | Slide |
|---|---|
| 1 | Title — Workforce Pell at SOU |
| 2 | SOU moment — we are asked for revenue ideas |
| 3 | What is Workforce Pell? |
| 4 | Why universities + state precedents (Virginia, Tennessee, etc.) |
| 5 | Why SOU specifically (bioregional + OHSU partnership) |
| 6 | RV occupations aligned to SOU strengths |
| 7 | HECC + WTDB authority + Kotek pull-quote |
| **8** | **Oregon's Prosperity Roadmap names this exact playbook** |
| 9 | Workforce Pell as public-private partnership |
| 10 | RV WIOA outcomes already exist |
| 11 | The data layer: Annotated Ledger → Ashland Intelligence |
| 12 | Anatomy of a SOU Workforce Pell program |
| 13 | Revenue model — conservative ramp with cost side |
| 14 | Cadence — four years, five phases |
| 15 | Ask 1 / 3 — SOU administration |
| 16 | Ask 2 / 3 — HECC + WTDB + Governor's Office |
| 17 | Ask 3 / 3 — Rogue Valley community & employers |
| 18 | Endorsed across the Rogue Valley (placeholders) |
| 19 | Sources & references |

## Editing

**HTML is master.** Open `sou_workforce_pell.html` in a browser to preview; edit inline. Style controlled by the `<style>` block at the top.

When making structural changes (slide order, new slide, deleted slide), update `sou_workforce_pell.tex` to match and re-export the PDF:

```sh
cd decks
xelatex -interaction=nonstopmode sou_workforce_pell.tex
xelatex -interaction=nonstopmode sou_workforce_pell.tex   # second pass for page refs
```

Requires xelatex + macOS system fonts (Times New Roman, Helvetica Neue, Menlo, Hoefler Text).

## Data citations

The deck draws numbers from these repo paths:
- `Statewide/oregon-wioa-dashboard/` — HECC WIOA outcomes (RV vs statewide, 2023)
- `RV Specific/Rogue Valley High-Wage, High-Demand, High-Skill Occupations 2024-2034.xlsx` — RV occupation demand & wages
- `Federal /workforce-pell-grants-a-strategic-opportunity-for-four-year-institutions.pdf` — Manhattan Inst. strategic framing
- `Federal /workforce-pell-grant-final-rule-fact-sheet-114075.pdf` — ED federal rule fact sheet
- `Statewide/2026 Oregon Talent Assessment.pdf` — ECOnorthwest for HECC

Plus the externally-cited `Oregon's Prosperity Roadmap` (Office of Governor Kotek, Dec 2025) — not stored in the repo; original at https://www.oregon.gov/gov/.

## Build artifacts (gitignored)

LaTeX intermediates (`.aux`, `.log`, `.nav`, `.out`, `.snm`, `.toc`, `.fls`, `.fdb_latexmk`, `.synctex.gz`) are excluded via `.gitignore` at the repo root. Only `.tex`, `.html`, and the canonical `.pdf` are tracked here.
