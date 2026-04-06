# Chapter 2 — Tutorial Direction
## Data Acquisition and Verification

**Football Analytics with Python · BarcaFutbol Analytics Course**

---

## What This Chapter Is About

Chapter 2 teaches the single habit that separates trustworthy analytics
from analytics that looks trustworthy. That habit is verification —
checking your data systematically before you build anything from it.

The chapter is structured as a live data cleaning session. Students start
with a deliberately broken dataset and fix it step by step. By the end,
they have a clean, verified CSV and two charts built from data they trust.

---

## Three Files Delivered

| File | Purpose |
|------|---------|
| `Chapter_02_Data_Acquisition_and_Verification.ipynb` | The Colab notebook |
| `data/raw_player_export.csv` | Deliberately messy raw data with 6 problems |
| `data/players_clean.csv` | The expected clean output (reference) |

---

## The Six Problems in the Raw Data

Students find and fix these in order:

| # | Problem | Column | Fix |
|---|---------|--------|-----|
| 1 | Duplicate row | All | `.drop_duplicates(keep='first')` |
| 2 | Impossible value | `G` | `.loc[condition, col] = corrected_value` |
| 3 | Missing values | `xG`, `KP` | `.fillna(column_mean)` |
| 4 | Abbreviations | All columns | `.rename(columns={})` |
| 5 | Season format | `Ssn` | `.str.replace('-', '/')` |
| 6 | Raw totals | All stats | `(total / minutes) * 90` |

---

## Learning Objectives

A student is ready for Chapter 3 if they can:

- [ ] Explain what each of the six data problems is and why it matters
- [ ] Write code to detect duplicate rows
- [ ] Correct a value in a specific cell using `.loc[]`
- [ ] Fill missing values using `.fillna()`
- [ ] Rename columns using a dictionary with `.rename()`
- [ ] Calculate a per-90 rate from a raw total and minutes played
- [ ] Read the completeness heatmap and describe what it shows
- [ ] Explain why we never overwrite the raw data file

---

## Key Concepts to Emphasise

**The audit-first mindset:** Before writing cleaning code, read the raw data
visually. Make a list of problems. Then fix them one by one. Never start
cleaning without knowing what you are fixing.

**Raw vs clean files:** Always keep the raw file untouched. The clean file
is the product of your work. If you discover an error in your cleaning process,
you can always rebuild the clean file from the raw one.

**Imputation is a decision, not a fix:** Filling missing values with the column
mean is an estimate, not real data. It must be documented. In a published analysis,
any imputed value should be noted — "Amir Hassan's xG is estimated."

**Triple verification:** After every calculation, verify at least three values
by hand. This catches errors in the formula before they propagate into charts.

---

## Common Student Mistakes

**Overwriting the raw file:** Students sometimes save over `raw_player_export.csv`
instead of creating `players_clean.csv`. Emphasise: raw data is sacred.

**Forgetting to re-run cells after fixing:** If a student fixes a value in
Cell 6 but forgets to re-run Cell 10 (per-90 calculation), the chart will
use the uncorrected value. The fix is always: run all cells in order.

**Not understanding NaN:** When Python encounters a missing value, it displays
`NaN` (Not a Number). Operations on NaN return NaN. `5 + NaN = NaN`. This is
why missing values must be addressed before any calculation.

---

## How This Chapter Connects Forward

| Chapter 2 introduces... | Used in... |
|-------------------------|-----------|
| `pd.read_csv()` with messy data | Every chapter |
| `.drop_duplicates()` | Any time you work with real data |
| `.fillna()` | Chapter 14 (career modelling with incomplete seasons) |
| `.rename(columns={})` | Every chapter |
| Per-90 calculation | Every chapter |
| Completeness heatmap | Chapter 10 (heat maps) — same technique, different data |
| Triple verification habit | Every chapter — becomes automatic |

---
*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
