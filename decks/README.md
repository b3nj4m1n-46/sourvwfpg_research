# Decks

LaTeX/Beamer presentation source files.

| File | Audience | Status |
|------|----------|--------|
| `sou_workforce_pell.tex` | SOU officials + community + (secondary) HECC/WTDB | Draft — pre-publication |

## Building

Requires xelatex and the Libertinus OTF fonts (Serif, Sans, Mono, SerifDisplay).

```sh
cd decks
latexmk -xelatex sou_workforce_pell.tex
```

## Notes

- The dark navy / cream / oil-accent visual system originated in a companion deck (`south_fusion.tex`, kept locally outside the repo).
- Optional includes: `facts.tex` (recurring values) and `_deck_theme.tex` (light/dark toggle). Both load via `\InputIfFileExists` so absence is fine.
- Data citations point back to files in `Statewide/` and `RV Specific/`.
