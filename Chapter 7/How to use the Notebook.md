# Chapter 7 — Tutorial Direction
## Radar Charts

**Football Analytics with Python · BarcaFutbol Analytics Course**

---

## What This Chapter Is About

Chapter 7 teaches radars from the geometry up. Before any chart code is written,
students understand polar coordinates — what theta and radius mean, why the polygon
must be closed, and how `np.linspace(0, 2*np.pi, n, endpoint=False)` divides the
circle into equal slices. This foundation means students can debug any radar problem
because they understand what is being drawn.

The `build_radar()` template handles single and dual player radars with one function,
making any comparison a three-line call.

---

## Three Files Delivered

| File | Purpose |
|------|---------|
| `Chapter_07_Radar_Charts.ipynb` | The Colab notebook |
| `data/chapter07_players.csv` | 11-player season stats |
| `TUTORIAL_DIRECTION.md` | This document |

---

## Learning Objectives

A student is ready for Chapter 8 if they can:

- [ ] Explain polar coordinates (theta and radius) in plain English
- [ ] Explain why `angles + angles[:1]` is necessary
- [ ] Create a polar axes with `subplot_kw=dict(polar=True)`
- [ ] Draw grid rings, the outer boundary, and spoke lines
- [ ] Normalise raw values to 0-100 using group maximums
- [ ] Add vertex dot markers at each metric point
- [ ] Call `build_radar()` for a single player and for a dual comparison

---

## The Closing Polygon — The Most Common Mistake

If a student's radar looks like a C instead of a closed shape, they forgot to close
the polygon. The fix is always:

```python
angles_closed = angles + angles[:1]   # 7 points, not 6
values_closed  = values + values[:1]   # last = first
```

`ax.plot(angles_closed, values_closed)` draws a line from each point to the next.
The 7th point is identical to the 1st, so the line closes back to the start.
Without it, matplotlib draws from the 6th point to... nothing.

---

## Normalisation — Raw vs Percentile

In this course we normalise to group maximum:
`normalised = min(raw / group_max * 100, 100)`

This means "what percentage of the best value in this group is this player?"
A normalised value of 80 means the player is 80% as good as the best player
in the group on that metric.

The alternative — true percentile ranks — requires a reference database.
Chapter 11 (Percentile Ranking) teaches this properly. For Chapters 7 and 8,
group-maximum normalisation is sufficient and honest.

---

## Radar vs Pizza — When to Use Each

| Radar (Chapter 7) | Pizza (Chapter 8) |
|-------------------|-------------------|
| 4–8 metrics | 8–12 metrics |
| Best for direct player vs player | Best for complete single-player profile |
| Same colour for all metrics | Colour by metric category (attacking/passing/defensive) |
| Overlapping polygons show difference clearly | Wedge sizes show strength/weakness at a glance |
| Used in: tactical comparison, scouting reports | Used in: newsletters, player profiles, season reviews |

---

## Common Mistakes

**Q: My radar has a grid but the spokes are missing.**
A: Spokes are separate lines from the centre to the outer ring. Add them with:
```python
for angle in angles:
    ax.plot([angle, angle], [0, 100], color=WHITE, alpha=0.08, linewidth=0.5)
```

**Q: The category labels are inside the chart, not outside.**
A: Label position is set by the radius. Use `ax.text(angle, 122, ...)` — the 122
places the label beyond the outer boundary (at 100). If labels appear inside,
the radius value is too low (below 100).

**Q: `ax.grid(False)` is not removing the polar grid.**
A: Polar axes have a default grid that persists. You need both
`ax.set_yticks([])` and `ax.grid(False)` to remove all automatic gridlines.
Then add your own grid rings manually with `ax.plot()`.

---

## How This Connects Forward

| Chapter 7 introduces... | Used in... |
|-------------------------|-----------|
| `build_radar()` | Chapter 16 (player comparison — 3 radar sections) |
| Polar axes | Chapter 8 (pizza — same axes type, different geometry) |
| Normalisation to group max | Chapter 11 (percentile ranking — more rigorous version) |
| Dual overlay on one axes | Chapter 17 (match review — team comparison radars) |

---
*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
