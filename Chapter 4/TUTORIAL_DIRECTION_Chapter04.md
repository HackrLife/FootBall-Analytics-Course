# Chapter 4 — Tutorial Direction
## Tables That Tell Stories

**Football Analytics with Python · BarcaFutbol Analytics Course**

---

## What This Chapter Is About

Chapter 4 teaches the most underused skill in data analytics: building a
table that communicates as clearly as a chart. Most analysts either ignore
tables entirely or produce raw DataFrames that look like spreadsheets from
2003. This chapter fixes that.

The centrepiece is `build_stats_table()` — a reusable function that takes
any DataFrame and produces a publication-ready styled table in one call.
The HTML export in Part 7 means the table can be dropped directly into
Ghost, Beehiiv, or Substack without any reformatting.

---

## Three Files Delivered

| File | Purpose |
|------|---------|
| `Chapter_04_Tables_That_Tell_Stories.ipynb` | The Colab notebook |
| `data/chapter04_players.csv` | Chapter 3 data + rank, form columns |
| `TUTORIAL_DIRECTION.md` | This document |

---

## The Two New Data Columns

**`rank`** — position in the group by GI/90. Calculated with `.rank()`.
Students learn how `.rank()` works and verify it matches the pre-calculated column.

**`form`** — last 5 match results as a string (`W W W D W`).
This column exists to demonstrate something charts cannot do: display mixed
data types. A string like `W W W D W` cannot go on a bar chart. A table
handles it naturally.

---

## Learning Objectives

A student is ready for Chapter 5 if they can:

- [ ] Explain when a table is the better choice over a chart
- [ ] Use `.style.format()` to control number display
- [ ] Use `.background_gradient()` to colour cells by value
- [ ] Use `.applymap()` with a custom function to colour specific cells
- [ ] Use `.highlight_max()` and `.highlight_min()` for outlier emphasis
- [ ] Call `build_stats_table()` with any DataFrame and get a styled result
- [ ] Export a styled table to HTML using `.to_html()`
- [ ] Use `.rank()` to calculate a rank column from any numeric column

---

## Key Concepts to Emphasise

### Tables and charts answer different questions

This is the most important analytical concept in Chapter 4. Students often
think charts are always better because they look more sophisticated. The
decision framework from the intro table should become automatic:

- **Exact numbers needed?** → Table
- **Mixed data types (text + numbers)?** → Table
- **Pattern or trend?** → Chart
- **Single metric across many players?** → Chart
- **Multiple metrics simultaneously?** → Table

### The `applymap` vs `apply` distinction

`.applymap()` applies a function to each individual cell.
`.apply()` applies a function to each row or column.

For tier colouring, we use `.applymap()` because we are colouring
one cell at a time based on that cell's value.

For a more complex operation — like highlighting an entire row if the player
is in the top 3 — we would use `.apply(axis=1)`.

### CSS in pandas styling

The `.set_table_styles()` and `.set_properties()` methods use CSS strings.
Students who have any web experience will recognise `background-color`,
`font-size`, `padding`, `border`. Students who have no web experience should
understand that CSS is just a way of describing how something looks — the syntax
is different from Python but the concept is the same as the colour palette.

### HTML export is publication-ready

The HTML that `.to_html()` produces is a complete, self-contained table.
It can be pasted into any HTML-capable newsletter platform. The styling
is embedded inline (not in a separate CSS file), which means it works in
email clients that strip external stylesheets.

---

## Common Student Mistakes

**Q: My `.background_gradient()` is showing all the same colour.**
A: This happens when all values in the column are identical or when `vmin == vmax`.
Check that the column actually has variation. Print `df[col].describe()` first.

**Q: `.applymap()` gives a deprecation warning in newer pandas.**
A: In pandas 2.1+, `.applymap()` was renamed to `.map()`. If students see this
warning, the fix is to replace `.applymap(fn, subset=[col])` with
`.map(fn, subset=[col])`. Both work in the versions used by this course.

**Q: The HTML export looks different in my email client.**
A: Email clients strip many CSS properties. Background colours generally
survive in Gmail. Font sizes and borders are less reliable. For maximum
compatibility, use the simplest possible styling in HTML exports.

**Q: `build_stats_table()` is not producing a gradient.**
A: Check that `gradient_col` is the exact column name in the DataFrame,
and that the column is numeric (not object/string type).

---

## How This Chapter Connects Forward

| Chapter 4 introduces... | Used in... |
|-------------------------|-----------|
| `build_stats_table()` | Chapter 16 (player comparison) — summary tables |
| `df.style` API | Chapter 18 (scout report) — stats tables |
| HTML export | Chapter 19 (publishing) — newsletter tables |
| `.rank()` | Chapter 11 (percentile ranking) — ranking systems |
| Chart + table pairing | Every chapter with complex analysis |
| `overperformance` column | Chapter 13 (xG analysis) — full treatment |

---
*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
*[github.com/HackrLife/Football-Analytics](https://github.com/HackrLife/Football-Analytics)*
