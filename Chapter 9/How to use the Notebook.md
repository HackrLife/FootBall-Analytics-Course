# Chapter 9 — Tutorial Direction: Scatter Plots

## What This Chapter Is About
Two metrics simultaneously on one chart. The scatter plot is where football analytics moves from describing one thing at a time to understanding relationships between things. The chapter builds in four layers: basic scatter → quadrant chart → glow halo highlight → diagonal line for expected vs actual.

## Three Files Delivered
| File | Purpose |
|------|---------|
| `Chapter_09_Scatter_Plots.ipynb` | The Colab notebook |
| `data/chapter09_scatter.csv` | 11 players, attacking + defensive stats + overperformance |
| `TUTORIAL_DIRECTION.md` | This document |

## Learning Objectives
- [ ] Plot a basic scatter with `ax.scatter()` and `ax.annotate()`
- [ ] Add quadrant lines using `ax.axvline()` and `ax.axhline()` at group averages
- [ ] Apply the glow halo technique with 3 concentric scatter calls
- [ ] Draw the diagonal reference line for xG vs Goals analysis
- [ ] Use `zorder` to control layering of overlapping elements
- [ ] Call `build_scatter()` template with any two metrics

## The Glow Halo — Three Calls, One Effect
```python
ax.scatter(x, y, s=700, color=c, alpha=0.15, zorder=5)  # outer glow
ax.scatter(x, y, s=380, color=c, alpha=0.28, zorder=6)  # mid ring
ax.scatter(x, y, s=200, color=c, alpha=1.00, zorder=7)  # solid core
```
The three sizes and opacities create a radiant effect. The increasing zorder ensures each layer draws on top of the previous. This pattern is used in the BarcaFutbol Yamal vs Saka scatter plots.

## The Diagonal Line — When to Use It
`y = x` (the line where actual equals expected) is only meaningful when X and Y measure the same thing at different times or different versions of the same concept — most commonly xG/90 (expected) vs Goals/90 (actual). Do not use a diagonal reference line for metrics that are inherently different scales.

## Common Mistakes
**Labels overlap**: Use individual per-player offset tuples `(ox, oy)` rather than a fixed offset. The `build_scatter()` template supports this via the offset dict pattern.
**Quadrant lines at wrong position**: Always calculate `avg_x = df[x_col].mean()` from the data — never hardcode a threshold unless you have an analytical reason for a specific value.

## How This Connects Forward
| Chapter 9 introduces... | Used in... |
|-------------------------|-----------|
| `build_scatter()` | Chapter 16 (player comparison — 2 scatter charts) |
| Glow halo technique | Chapter 16 (peer group scatter) |
| Diagonal line | Chapter 13 (xG analysis — expected vs actual) |
| Quadrant labels | Chapter 18 (scout report — player positioning) |

*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
