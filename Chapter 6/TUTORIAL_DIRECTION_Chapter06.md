# Chapter 6 — Tutorial Direction
## Bar Charts for Comparison

**Football Analytics with Python · BarcaFutbol Analytics Course**

---

## What This Chapter Is About

Chapter 6 makes the case that the bar chart — the simplest chart in any analyst's
toolkit — is also the most frequently built incorrectly. Wrong orientation, no
average line, no value labels, wrong colour strategy. This chapter fixes all of it.

Three bar chart types are built in sequence, each answering a different analytical
question. The `build_bar_chart()` template at the end covers 80% of bar chart use
cases in one reusable function.

---

## Three Files Delivered

| File | Purpose |
|------|---------|
| `Chapter_06_Bar_Charts_for_Comparison.ipynb` | The Colab notebook |
| `data/chapter06_players.csv` | 11-player season stats |
| `TUTORIAL_DIRECTION.md` | This document |

---

## Learning Objectives

A student is ready for Chapter 7 if they can:

- [ ] Explain why horizontal bars are better than vertical for player names
- [ ] Add an average reference line using `ax.axvline()`
- [ ] Add value labels at the end of each bar using `ax.text()`
- [ ] Choose between player colours and tier colours for a given question
- [ ] Build a grouped bar chart with `y + h/2` and `y - h/2` offsets
- [ ] Call `build_bar_chart()` with any metric and colour strategy

---

## The Three Bar Chart Types

| Type | When to Use | Colour Strategy |
|------|-------------|----------------|
| Single metric + average line | "Who leads on X?" | Player identity colours |
| Tier-coloured | "What is the distribution of quality?" | TIER_COLORS dict |
| Grouped | "How does each player split between two metrics?" | One colour per metric |

---

## Key Concepts

### The average line is not optional

`ax.axvline(x=avg, color=GOLD, linestyle='--', alpha=0.55)` is the single most
analytically useful addition to any bar chart. Without it, the reader must mentally
calculate the average to understand whether a player's bar is good or poor.
With it, the analysis is instant — left of the line = below average, right = above.

### Sorting direction matters

`ascending=True` puts the lowest bar at the top, highest at the bottom. For charts
read top-to-bottom, this means the reader's eye moves from worst to best — the most
important player is at the bottom right where the longest bar ends. This is more
natural than the reverse, where the leader's bar is at the top left (shorter visual
travel to read the label, but longer to see the value).

Convention: sort ascending for horizontal bars (lowest at top, highest at bottom).

### The grouped bar offset formula

For two sub-bars per player:
```python
y = np.arange(len(players))  # centre position per player
h = 0.38                      # height of each sub-bar
ax.barh(y + h/2, values1, h)  # upper sub-bar
ax.barh(y - h/2, values2, h)  # lower sub-bar
ax.set_yticks(y)               # tick marks at centre positions
```
The `h/2` offset places the two bars symmetrically above and below the player's
centre line. For three sub-bars: `y + h`, `y`, `y - h`.

---

## Common Mistakes

**Q: My grouped bar chart has the y-axis labels at the wrong position.**
A: You must set `ax.set_yticks(y)` and `ax.set_yticklabels(player_names)` after
creating the bars. Without `set_yticks`, matplotlib auto-places ticks at 0, 1, 2...
which may not align with `y + h/2` and `y - h/2`.

**Q: Value labels are overlapping the bars or cut off by the axis limit.**
A: Set `ax.set_xlim(0, max_value * 1.20)` — this gives 20% padding on the right
for the labels. Adjust the multiplier if labels are still cut off.

---

## How This Connects Forward

| Chapter 6 introduces... | Used in... |
|-------------------------|-----------|
| `ax.axvline()` | Every subsequent chart with a reference line |
| Grouped bars | Chapter 17 (match review — team comparison bars) |
| `build_bar_chart()` | Chapter 16 (player comparison head-to-head section) |
| Tier colour strategy | Chapter 8 (pizza — value label tier colours) |

---
*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
