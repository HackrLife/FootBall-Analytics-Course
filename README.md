# Football Analytics with Python
### A Complete Course — From Zero to Publication-Ready Analysis

**By HackrLife Media LLC · BarcaFutbol Analytics**

> *You don't need to be a data scientist to think like one.*
> *You need to ask the right question, find the right data, and build the right chart.*
> *This course teaches all three — using football as the language.*

---

## Who This Course Is For

This course is for **anyone who loves football and is curious about data** —
regardless of prior Python experience.

If you have never written a line of code in your life, start at Chapter 1.
If you know some Python but have never built a data visualisation, start at Chapter 3.
If you can already build charts but want to learn how professional analysts think,
read Chapter 1 and jump to Chapter 11.

By the end of 20 chapters, you will be able to:

- Build 8 different types of professional football analytics charts
- Load, clean and verify real football data from public sources
- Frame an analytical argument — not just describe what happened, but explain what it means
- Publish your work on GitHub in a format that signals professional credibility
- Package and sell your analysis as a paid product

**No statistics degree required. No data science background required.**
Just Python, pandas, matplotlib, and a willingness to think carefully about football.

---

## The Course at a Glance

| Part | Chapters | What You Learn |
|------|----------|----------------|
| **I — Foundations** | 1–4 | Analytical thinking, data loading, design systems, tables |
| **II — Core Charts** | 5–10 | Line charts, bars, radars, pizza charts, scatter plots, heat maps |
| **III — Advanced Analysis** | 11–15 | Percentiles, correlation, xG, career modelling, clustering |
| **IV — The Full Project** | 16–20 | Player comparison, match review, scout report, publishing, portfolio |

**Each chapter:**
- Answers one real football question
- Teaches one skill
- Produces one reusable code template
- Takes 30–45 minutes to complete

---

## Chapter List

### PART I — FOUNDATIONS
*For absolute beginners. No prior Python knowledge assumed.*

| # | Chapter | Key Skill | What You Build |
|---|---------|-----------|----------------|
| 01 | [The Analytical Question](Chapter-01-The-Analytical-Question/) | Analytical framing | Your first chart + the design system |
| 02 | [Your First Dataset](Chapter-02-Your-First-Dataset/) | Data acquisition | A clean player comparison CSV |
| 03 | [Themes and Colour Palettes](Chapter-03-Themes-and-Colour-Palettes/) | Visual design | A reusable colour system for any analysis |
| 04 | [Tables That Tell Stories](Chapter-04-Tables-That-Tell-Stories/) | Pandas styling | A publication-ready stats table |

### PART II — CORE CHARTS
*One chart type per chapter. Fully reusable templates.*

| # | Chapter | Key Skill | What You Build |
|---|---------|-----------|----------------|
| 05 | [Line Charts and Career Arcs](Chapter-05-Line-Charts-Career-Arcs/) | Smoothed line charts | A career arc comparing two players |
| 06 | [Bar Charts for Comparison](Chapter-06-Bar-Charts-for-Comparison/) | Grouped bar charts | A head-to-head metrics bar chart |
| 07 | [Radar Charts](Chapter-07-Radar-Charts/) | Polar coordinates | A dual player radar — any 6 metrics |
| 08 | [Pizza Charts](Chapter-08-Pizza-Charts/) | Wedge geometry | A dual pizza profile — any 10 metrics |
| 09 | [Scatter Plots](Chapter-09-Scatter-Plots/) | Peer group analysis | A quadrant scatter with peer group |
| 10 | [Heat Maps](Chapter-10-Heat-Maps/) | 2D colour grids | A player performance heat map |

### PART III — ADVANCED ANALYSIS
*Going beyond charts into real analytical techniques.*

| # | Chapter | Key Skill | What You Build |
|---|---------|-----------|----------------|
| 11 | [Percentile Ranking](Chapter-11-Percentile-Ranking/) | Normalisation | A percentile benchmark system |
| 12 | [Correlation and Regression](Chapter-12-Correlation-Regression/) | Statistical relationships | A regression analysis with football data |
| 13 | [xG and Expected Metrics](Chapter-13-xG-and-Expected-Metrics/) | Expected value | An xG overperformance chart |
| 14 | [Career Trajectory Modelling](Chapter-14-Career-Trajectory-Modelling/) | Trend analysis | A career peak and decline model |
| 15 | [Clustering Players](Chapter-15-Clustering-Players/) | Machine learning basics | A player type cluster analysis |

### PART IV — THE FULL PROJECT
*Building a complete published analysis from scratch.*

| # | Chapter | Key Skill | What You Build |
|---|---------|-----------|----------------|
| 16 | [Building a Player Comparison](Chapter-16-Player-Comparison/) | Full analysis | 8 charts, one analytical argument |
| 17 | [Building a Match Review](Chapter-17-Match-Review/) | Match data | A complete match review chart suite |
| 18 | [Building a Scout Report](Chapter-18-Scout-Report/) | Positional analysis | A one-page scout report |
| 19 | [Publishing Your Work](Chapter-19-Publishing/) | Distribution | A GitHub repo + Beehiiv post |
| 20 | [Building Your Portfolio](Chapter-20-Your-Portfolio/) | Credibility signalling | A professional analytics portfolio |

---

## How to Use This Course

### Option 1 — Google Colab (Recommended for Beginners)
Click any chapter badge to open it directly in Google Colab.
No installation required. Just click, read, and run the cells.

[![Open Chapter 01 in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HackrLife/Football-Analytics/blob/main/The-Football-Analytics-Course/Chapter-01-The-Analytical-Question/Chapter_01_The_Analytical_Question.ipynb)

### Option 2 — View on nbviewer (Read Without Running)
See all charts rendered without running any code.

[▶ View Chapter 01 on nbviewer](https://nbviewer.org/github/HackrLife/Football-Analytics/blob/main/The-Football-Analytics-Course/Chapter-01-The-Analytical-Question/Chapter_01_The_Analytical_Question.ipynb)

### Option 3 — Clone the Repo (For Local Development)
```bash
git clone https://github.com/HackrLife/Football-Analytics.git
cd Football-Analytics/The-Football-Analytics-Course
pip install -r requirements.txt
jupyter notebook
```

---

## The Data

### What's Included in This Course

We have supplied two ready-to-use datasets that power all chapters in this course:

- **`barcafutbol_master.csv`** — the primary course dataset. Contains career statistics
  for Lamine Yamal and Bukayo Saka across multiple seasons, plus a 2025/26 peer group
  of 16 top European wide forwards. All values are per-90-minute averages.

- **`barcafutbol_match.csv`** — match-level data for the Atlético Madrid vs Barcelona
  La Liga fixture (April 2026), used in the match review chapters.

Both datasets have been compiled, cleaned and verified from professional football
data platforms including Sofascore, FotMob and Wyscout. They are ready to load
and use immediately — no data cleaning required.

### Where to Find Your Own Data

Once you have completed the course and want to build your own analyses,
here are the best free and public data sources:

| Source | What It Contains | Best For |
|--------|-----------------|----------|
| [StatsBomb Open Data](https://github.com/statsbomb/open-data) | Free event-level data for selected competitions | Advanced match analysis, xG models |
| [FBref](https://fbref.com) | Comprehensive player and team stats, all major leagues | Season stats, player comparison |
| [Kaggle Football Datasets](https://www.kaggle.com/datasets?search=football) | Community-curated datasets, historical data | Exploratory analysis, modelling |
| [football-data.co.uk](https://football-data.co.uk) | Historical match results and odds data | Regression, prediction models |
| [understat.com](https://understat.com) | xG data for top European leagues | Expected metrics analysis |
| [transfermarkt](https://transfermarkt.com) | Market values, career history, transfer data | Career arc, valuation analysis |

Chapter 2 walks through how to collect, structure and verify data from any of
these sources into a clean CSV ready for analysis.

---

## The Reusability Principle

Every chart in this course follows the same structure:

```python
# ── 1. DATA ─────────────────────────────────────────────
# Change these values to use any players, any stats
player_1_name   = 'Lamine Yamal'
player_2_name   = 'Bukayo Saka'
metric_values   = [88, 82, 92, 75, 72, 90]   # ← change these numbers

# ── 2. COLOURS ──────────────────────────────────────────
# Change these to match any team or publication brand
player_1_colour = '#A50044'   # ← change this hex code
player_2_colour = '#f0f6fc'   # ← change this hex code

# ── 3. CHART ────────────────────────────────────────────
# This section never changes — it is the reusable template
build_chart(player_1_name, player_2_name,
            metric_values, player_1_colour, player_2_colour)
```

**Three things to change. Everything else stays the same.**
By Chapter 7, you can produce a professional radar chart for any two players
in any league in under 5 minutes.

---

## The Design System

All charts in this course share a consistent visual identity —
the BarcaFutbol Analytics design system, explained fully in Chapter 3.

```python
# Copy this palette into any notebook — your charts will look professional

BG      = '#0d1117'   # background — near-black
WHITE   = '#f0f6fc'   # all text and labels
GRAY    = '#8b949e'   # grid lines and secondary text
GOLD    = '#EDBB00'   # accent colour and reference lines
GREEN   = '#4CAF50'   # elite performance  (≥ 70th percentile)
YELLOW  = '#ffd60a'   # average performance (40–69th percentile)
RED     = '#e63946'   # below average       (< 40th percentile)
```

Dark background. Clear hierarchy. Consistent performance tiers.
The same system used in charts that people pay to read.

---

## What Makes This Course Different

**Most data science courses teach skills.**
This course teaches skills *in service of arguments.*

Every chapter answers a real football question that had a genuinely uncertain
answer before the analysis was built. The student doesn't learn how to make
a radar chart — they learn how to use a radar chart to argue that Lamine Yamal's
attacking profile is statistically unprecedented for a player his age.

**Most football analytics content is descriptive.**
This course is argumentative.

There is a difference between saying *"Yamal scores 0.6 goals per 90"* and saying
*"Yamal converts above his expected goals by +0.19 — consistently, across two seasons —
which means the model undervalues his finishing ability."*

The first is a fact. The second is an insight. This course teaches you how to produce
the second from the first, every time.

---

## Roadmap — Coming Soon

- 🎥 **Video walkthroughs** — 15-minute video for each chapter, showing the
  notebook running live with analytical commentary
- 🎙️ **Audio episodes** — "The analytical question behind this chart" —
  10-minute podcast per chapter, no code required, just football thinking
- 📝 **Exercises** — build-it-yourself challenges at the end of each chapter,
  with a new dataset and a blank template
- 🏆 **Community showcase** — best student charts featured in the
  BarcaFutbol newsletter each month
- 🎓 **Full MOOC** — structured course with assessments, peer review,
  and a completion certificate

---

## About This Course

This course was built alongside the BarcaFutbol player comparison article
*"What Do You Get When You Pit Lamine Against Saka?"* — a 3,000-word
analytical piece with 8 original data visualisations, published April 2026.

Every chart in the course is a real chart from that real article.
Every analytical question is the actual question the analysis was trying to answer.
The course teaches you how the work was built — not a simplified version of it.

**BarcaFutbol** covers FC Barcelona through data, tactics, and long-form writing.
**HackrLife Media LLC** produces analytical content across football, AI, finance
and growth marketing.

---

## Requirements

```
matplotlib >= 3.8
scipy      >= 1.11
pandas     >= 2.0
numpy      >= 1.26
jupyter    >= 1.0
```

Install everything in one line:
```bash
pip install matplotlib scipy pandas numpy jupyter
```

---

## Licence

Code: **MIT** — use it, adapt it, build on it freely.
Written content and analysis: © 2026 HackrLife Media LLC / BarcaFutbol.

---

*Built with Python, matplotlib, and the conviction that anyone can learn
to think analytically about football — if you give them the right question.*

**[Start with Chapter 1 →](Chapter-01-The-Analytical-Question/)**
