# Chapter 10 — Tutorial Direction: Heat Maps

## What This Chapter Is About
A heat map turns a grid of numbers into a grid of colours. The chapter teaches the `plt.Rectangle` patch geometry, the colourmap + normalisation pipeline, and the luminance formula for automatic text colour. The `build_heatmap()` template covers performance-over-time, team comparison matrices, and data quality audits.

## Three Files Delivered
| File | Purpose |
|------|---------|
| `Chapter_10_Heat_Maps.ipynb` | The Colab notebook |
| `data/chapter10_heatmap.csv` | 11 players × 10 match ratings |
| `TUTORIAL_DIRECTION.md` | This document |

## Learning Objectives
- [ ] Build a heat map from `plt.Rectangle` patches
- [ ] Use `plt.cm.RdYlGn` and `plt.Normalize()` to map values to colours
- [ ] Add a colourbar legend with `plt.colorbar()`
- [ ] Use the luminance formula to auto-switch text colour
- [ ] Identify consistency patterns from match-by-match data
- [ ] Call `build_heatmap()` with any grid data

## The Luminance Formula
```python
luminance = 0.299*R + 0.587*G + 0.114*B
text_color = '#111111' if luminance > 0.5 else WHITE
```
This is the ITU-R BT.601 standard for perceived brightness. It weights green most heavily because the human eye is most sensitive to green. Never use `(R+G+B)/3` — that gives equal weight to all channels and produces incorrect brightness estimates.

## Colourmap Choices
| Cmap | Use case |
|------|----------|
| `RdYlGn` | Performance (red=poor, green=good) |
| `Blues` | Intensity (white=low, blue=high) |
| `RdBu_r` | Diverging (red=negative, blue=positive) |
| `YlOrRd` | Heat/frequency (yellow=low, red=high) |

## How This Connects Forward
| Chapter 10 introduces... | Used in... |
|-------------------------|-----------|
| `plt.Rectangle` patch | Chapter 8 pizza revisit |
| `build_heatmap()` | Chapter 18 (scout report — form matrix) |
| Luminance formula | Any chart with coloured cells needing text labels |
| `plt.Normalize()` | Chapter 12 (regression — colour by residual size) |

*© 2026 HackrLife Media LLC · BarcaFutbol Analytics Course*
