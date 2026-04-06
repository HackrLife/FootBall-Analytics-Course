# Chapter 3 — Tutorial Direction
## Themes and Colour Palettes

**Football Analytics with Python · BarcaFutbol Analytics Course**

---

## What This Chapter Is About

Chapter 3 does something no other data analytics course does: it treats design
as an analytical discipline, not an aesthetic preference. Every decision — the
background colour, the opacity of a grid line, whether to show 2 or 4 chart
borders — is justified with a reason that connects to how the human brain
processes visual information.

The centrepiece of this chapter is `style_axis()` — a reusable function that
applies the full BarcaFutbol design system to any chart in a single line.
From Chapter 4 onward, every notebook imports this function.

---

## Three Files Delivered

| File | Purpose |
|------|---------|
| `Chapter_03_Themes_and_Colour_Palettes.ipynb` | The Colab notebook |
| `data/chapter03_players.csv` | Chapter 2 data + tier and percentile columns |
| `TUTORIAL_DIRECTION.md` | This document |

---

## Learning Objectives

A student is ready for Chapter 4 if they can:

- [ ] Explain the 8-second rule and what it means for chart design
- [ ] Name the five design decisions that matter most, and explain why each one
- [ ] Explain what a pre-attentive attribute is and give two examples
- [ ] Explain why we give each player a unique colour across all charts
- [ ] Write the `style_axis()` function from memory (or understand every line of it)
- [ ] Explain when to use player colours vs tier colours
- [ ] Build a chart in light theme by changing one parameter
- [ ] Explain why we pair tier colours with text labels for accessibility

---

## Key Concepts — What to Emphasise

### Design is speed, not beauty

The goal of every design decision is to reduce the time between "reader looks
at chart" and "reader understands insight." Dark background increases contrast
(faster extraction). Removing top/right spines reduces visual noise (less to decode).
Subtle grid lines help the eye measure without competing with data (better signal/noise).
Each decision saves a fraction of a second. Across a chart that 10,000 people read,
those fractions matter.

### The DRY principle in action

`style_axis()` is the student's first real experience of the DRY principle
(Don't Repeat Yourself). The function is 30 lines that previously appeared
8–10 times per notebook, slightly differently each time. Centralising it means
a single change to `style_axis()` propagates to every chart. This is how
professional code is written.

### Colour carries meaning — or it doesn't

There are two different colour strategies in this course, and confusing them
is a common mistake:
- **Player identity colours** (PLAYER_COLORS dict) — consistent across charts,
  pre-attentive association, used when tracking individuals
- **Performance tier colours** (TIER_COLORS dict) — communicate quality level,
  used when characterising a group distribution

A student who understands when to use which is thinking analytically, not just
decoratively.

### Accessibility is not optional

8% of men have colour vision deficiency. Designing for accessibility is not
a concession — it makes charts better for everyone by forcing you to pair
colour with labels, size, and position as redundant channels.

---

## The Before / After Moment

The side-by-side before/after in Part 5 is the emotional core of this chapter.
Students should spend time with it. The invitation is to count the specific
changes and connect each one to a reason listed in the table.

The insight that should land here: **the designed chart took 5 additional decisions
and maybe 15 additional lines of code. It communicates completely differently.**
That ratio — small code cost, large communication gain — is what makes design
worth learning.

---

## Common Student Questions

**Q: Can I use these colours in my own publications?**
A: Yes. The design system is MIT licensed — use it, adapt it, make it your own.
The only ask is that if you share your work publicly, you don't claim it was
built with different tools than you actually used.

**Q: What if my club's colours clash with the dark background?**
A: Some colours (very dark navy, black) disappear on a dark background. The fix
is to add a slight luminosity boost: `colour + 20% lightness`. In practice, most
club colours work on dark backgrounds. The ones that don't work are those that
are close to the background colour itself — very dark green, very dark navy.

**Q: Why don't we just use seaborn or plotly? They look better by default.**
A: Seaborn and Plotly are excellent libraries and you should learn them after
this course. We use matplotlib because it teaches the underlying primitives —
understanding how `ax.spines['top'].set_visible(False)` works means you can do
it in any library, not just matplotlib. The transfer of knowledge goes one way:
matplotlib → everything else. Not the reverse.

**Q: The `style_axis()` function doesn't handle the `x` vs `y` grid separately.**
A: Correct — it applies grid to all axes. For horizontal bar charts, you might
want `ax.grid(True, axis='x')` to show only vertical grid lines. This is a valid
extension of the function. Exercise 3 points students toward extending the function
themselves — adding `spine_width` is the first step. Adding `grid_axis` is a
natural next exercise.

---

## How This Chapter Connects Forward

| Chapter 3 introduces... | Used in... |
|-------------------------|-----------|
| `style_axis()` function | Every chapter from 4 onward |
| `TIER_COLORS` dict | Chapter 8 (pizza charts) — metric quality tiers |
| `PLAYER_COLORS` dict | Every chapter with multiple players |
| Dark vs light theme | Chapter 19 (publishing) — choosing theme for platform |
| Pre-attentive attributes | Chapter 9 (scatter — glow halo for focus players) |
| Colour + label redundancy | Chapter 8 (pizza — value labels + colour tiers) |

---

## The `style_axis()` Function — Complete Reference

Students should copy this function into every notebook they build.
From Chapter 4 onward, it is assumed to be defined.

```python
def style_axis(ax, theme='dark', xlabel=None, ylabel=None,
               title=None, subtitle=None):
    if theme == 'dark':
        bg = BG; text_col = WHITE
        grid_col = WHITE; spine_col = GRAY
    else:
        bg = '#f8f9fa'; text_col = '#1a1a2e'
        grid_col = '#cccccc'; spine_col = '#888888'

    ax.set_facecolor(bg)
    ax.spines['bottom'].set_color(spine_col)
    ax.spines['left'].set_color(spine_col)
    ax.spines['top'].set_visible(False)
    ax.spines['right'].set_visible(False)
    ax.tick_params(colors=text_col, labelsize=10)
    ax.grid(True, alpha=0.07, color=grid_col, linewidth=0.8)

    if xlabel:
        ax.set_xlabel(xlabel, color=text_col, fontsize=11, labelpad=8)
    if ylabel:
        ax.set_ylabel(ylabel, color=text_col, fontsize=11, labelpad=8)
    if title and subtitle:
        ax.set_title(f'{title}\n{subtitle}', color=text_col,
                     fontsize=13, fontweight='bold', pad=15, linespacing=1.6)
    elif title:
        ax.set_title(title, color=text_col, fontsize=13,
                     fontweight='bold', pad=12)
    return ax
```

---
*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
*[github.com/HackrLife/Football-Analytics](https://github.com/HackrLife/Football-Analytics)*
