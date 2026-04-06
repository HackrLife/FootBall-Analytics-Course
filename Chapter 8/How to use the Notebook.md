# Chapter 8 — Tutorial Direction
## Pizza Charts

**Football Analytics with Python · BarcaFutbol Analytics Course**

---

## What This Chapter Is About

Chapter 8 teaches the pizza chart — the most reader-friendly chart type in
football analytics publishing. Where radars are for analysts and coaches, pizzas
are for everyone. The colour coding by metric category (attacking/passing/defensive),
the centre badge with the player name, and the wedge-size-as-percentile design make
pizzas immediately understandable without any explanation.

The chapter teaches the Wedge geometry from first principles before building
the pizza, so students understand exactly what each parameter does.

---

## Three Files Delivered

| File | Purpose |
|------|---------|
| `Chapter_08_Pizza_Charts.ipynb` | The Colab notebook |
| `data/chapter08_players.csv` | 11-player season stats |
| `TUTORIAL_DIRECTION.md` | This document |

---

## Learning Objectives

A student is ready for Chapter 9 if they can:

- [ ] Explain the `Wedge(centre, radius, theta1, theta2)` parameters
- [ ] Calculate wedge angles: `90 - i*(360/n)` and `t1 - (360/n)`
- [ ] Normalise raw values to a 0.28–0.88 radius range
- [ ] Colour wedges by analytical category
- [ ] Add a centre badge using `Circle` patch
- [ ] Add value labels at the correct angle position
- [ ] Call `draw_pizza()` and `build_dual_pizza()` for any player

---

## The Wedge Geometry

```
radius = 0.28 + (raw / group_max) * 0.60
```

- `0.28` — the inner radius (minimum wedge size, even for 0%)
- `0.60` — the range of the wedge extension (0.28 to 0.88)
- `0.88` — the outer radius at 100% (matches the outer grid ring)

The inner radius of 0.28 ensures even the weakest metrics have a small visible
wedge. Setting it to 0 would make weak metrics invisible — analytically dishonest.

---

## Category Colours — Design Reasoning

| Category | Colour | Why |
|----------|--------|-----|
| Attacking | `#EDBB00` Gold | The premium category — goals, shots, dribbles |
| Passing | `#4CAF50` Green | Creation and ball retention — positive association |
| Defensive | `#3498DB` Blue | Defensive solidity — cool, structured feeling |

The reader learns this system in Chapter 3 and it is consistent across all pizzas
in the course. By Chapter 8, colour recognition is pre-attentive — the reader
sees "attacking cluster" before reading any labels.

---

## The Centre Badge

```python
Circle((0,0), 0.25, facecolor=BG2, edgecolor=player_colour, linewidth=2.5)
```

The centre badge serves three purposes:
1. Hides the inner ends of the wedges where they converge (which looks messy)
2. Provides a natural location for the player name
3. Uses the player's identity colour as the border — connecting the pizza to the player

---

## Common Mistakes

**Q: My wedges are all the same size regardless of the data.**
A: Check that `pct = min(raw / group_max, 1.0)` is computing correctly.
Print `pct` for each metric before drawing. If `pct` is 0 for all metrics,
`group_max` is likely 0 or the column names don't match.

**Q: My category labels overlap with the wedge value labels.**
A: The outer label is at radius `1.10` and the value label at `0.92`.
If they overlap, the metric label is too long. Use `\n` to split it onto
two lines: `'Goals\n/90'` instead of `'Goals/90'`.

**Q: The centre circle is not centred.**
A: `Circle((0,0), ...)` draws at (0,0). Check that `ax.set_xlim(-1.35, 1.35)`
and `ax.set_ylim(-1.35, 1.35)` are both set and equal. Unequal limits
will distort the circle into an ellipse.

---

## How This Connects Forward

| Chapter 8 introduces... | Used in... |
|-------------------------|-----------|
| `draw_pizza()` | Chapter 16 (player comparison — full season profile) |
| `build_dual_pizza()` | Chapter 18 (scout report — side-by-side profiles) |
| `Wedge` patch | Chapter 10 (heat maps — alternative to rectangles) |
| Category colour system | Consistent throughout all subsequent chapters |
| Centre badge pattern | Chapter 17 (match review — team badge in radar centre) |

---
*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
