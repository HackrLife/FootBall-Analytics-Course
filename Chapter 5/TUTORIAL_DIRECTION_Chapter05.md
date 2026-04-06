# Chapter 5 — Tutorial Direction
## Line Charts and Career Arcs

**Football Analytics with Python · BarcaFutbol Analytics Course**

---

## What This Chapter Is About

Chapter 5 teaches the career arc — the most honest chart in football analytics.
Raw per-season points connected by a smoothed cubic spline that passes exactly
through each data point but curves between them. The result is a professional
trajectory chart that shows not just where a player is now but where they have been
and, by implication, where they are heading.

The centrepiece is `build_career_arc()` — a reusable template that accepts any
players and any metric and handles all the smoothing, annotation, and styling.

---

## Three Files Delivered

| File | Purpose |
|------|---------|
| `Chapter_05_Line_Charts_Career_Arcs.ipynb` | The Colab notebook |
| `data/chapter05_careers.csv` | Multi-season career data for 6 players |
| `TUTORIAL_DIRECTION.md` | This document |

---

## The Dataset

`chapter05_careers.csv` has 31 rows — season-by-season career data for six players
across different career lengths (2 to 8 seasons). This unevenness is intentional:
students must handle players with different numbers of data points, which is exactly
the real-world problem. The `k=min(3, len(x)-1)` fallback in `smooth_career()`
handles players with fewer than 4 seasons gracefully.

---

## Learning Objectives

A student is ready for Chapter 6 if they can:

- [ ] Explain what cubic spline interpolation does in plain English
- [ ] Write `smooth_career(x, y)` from memory (4 lines)
- [ ] Plot a single smoothed career arc with fill and vertex dots
- [ ] Overlay multiple players on one polar axis with individual colours
- [ ] Call `build_career_arc()` with different players and metrics
- [ ] Name the four career arc archetypes and give an example of each

---

## The Four Career Arc Archetypes

Every career arc is one of these four shapes. Teaching students to name them
before building the chart gives them a vocabulary for analysis:

| Archetype | Shape | Example in dataset |
|-----------|-------|-------------------|
| **Rising** | Consistent upward slope, no peak yet | Marcus Silva |
| **Peak and plateau** | Rise → flat → gradual decline | Diego Varela |
| **Flat and consistent** | Near-horizontal, entered at high level | Lucas Ferreira |
| **V-shaped recovery** | Dip in one season, then bounce back stronger | Amir Hassan |

---

## Key Concepts

### Why smooth at all?

Raw seasonal data connects discrete points with straight lines — the result is a
zigzag that is hard to read as a trajectory. The smoothed spline shows the underlying
career shape, making it immediately obvious whether a player is rising, declining,
or plateauing. Both versions plot the same raw dots — the smoothing only affects
the line between them.

### The `k=min(3, len-1)` safety

`make_interp_spline(x, y, k=3)` requires at least 4 data points. For younger players
with 2 or 3 seasons, `k=min(3, len(x)-1)` degrades gracefully to linear (k=1) or
quadratic (k=2) rather than throwing an error.

### End-of-line player labels

We annotate the last data point with the player name rather than using a legend.
This reduces eye movement — the reader does not need to look from the chart to a
legend box and back. The label sits exactly where the line ends.

---

## Common Mistakes

**Q: My spline is producing wild oscillations between points.**
A: This happens when data points are very close together in x with very different y
values. The fix is to use `k=2` (quadratic) instead of `k=3` (cubic) for that player,
or to check that the data is sorted by age before smoothing.

**Q: The fill_between goes below zero.**
A: Add `ax.set_ylim(bottom=0)` after the plot call. Or use
`ax.fill_between(xs, np.maximum(ys, 0), ...)` to clip the fill at zero.

**Q: Player labels overlap each other at the end of the chart.**
A: Adjust `xytext=(last['age'] + 0.3, last[metric] + offset)` where offset differs
per player. Or use only the first name with `player.split()[0]`.

---

## How This Connects Forward

| Chapter 5 introduces... | Used in... |
|-------------------------|-----------|
| `smooth_career()` | Chapter 14 (career trajectory modelling) |
| `build_career_arc()` | Chapter 16 (player comparison — career arc section) |
| `fill_between()` | Chapter 13 (xG — area between actual and expected) |
| Career archetypes | Chapter 14 (peak age modelling) |
| End-of-line annotation | Chapter 9 (scatter — player labels at dot positions) |

---
*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
