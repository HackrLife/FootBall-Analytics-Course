# Football Analytics with Python
### A Complete Course — From Zero to Publication-Ready Analysis

**By HackrLife · BarcaFutbol Analytics**

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
Click any chapter badge below to open it directly in Google Colab.
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

## The Reusability Principle

Every chart in this course follows the same structure:

```python
# ── 1. DATA ─────────────────────────────────────────────
# Change these values to use any players, any stats
player_1_name = 'Lamine Yamal'
player_2_name = 'Bukayo Saka'
metric_values = [88, 82, 92, 75, 72, 90]   # ← change these

# ── 2. COLOURS ──────────────────────────────────────────
# Change these to match any team or publication
player_1_colour = '#A50044'   # ← change this
player_2_colour = '#f0f6fc'   # ← change this

# ── 3. CHART ────────────────────────────────────────────
# This section never changes — it is the reusable template
build_chart(player_1_name, player_2_name, metric_values,
            player_1_colour, player_2_colour)
```

**Three things to change. Everything else stays the same.**
By Chapter 7, you can produce a professional radar chart for any two players
in any league in under 5 minutes.

---

## The Design System

All charts in this course share a consistent visual identity — the
BarcaFutbol Analytics design system, explained fully in Chapter 3.

```python
# Copy this palette into any notebook and your charts will look professional

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

## The Data

All chapters use real football statistics sourced from
[Sofascore](https://sofascore.com), cleaned and verified.

The master dataset (`data/barcafutbol_master.csv`) contains:
- Lamine Yamal — 4 seasons of career data (2022/23–2025/26)
- Bukayo Saka — 8 seasons of career data (2018/19–2025/26)
- 14 peer wide forwards — 2025/26 season data for scatter plot peer groups

All values are **per 90 minutes** — the correct unit for player comparison
regardless of minutes played or games started.

---

## What Makes This Course Different

**Most data science courses teach skills.**
This course teaches skills *in service of arguments.*

Every chapter answers a real football question that had a genuinely uncertain
answer before the analysis was built. The student doesn't learn how to make a
radar chart — they learn how to use a radar chart to argue that Lamine Yamal's
attacking profile is statistically unprecedented for a player his age.

The difference sounds subtle. The results are not.

**Most football analytics content is descriptive.**
This course is argumentative.

---

## Roadmap — Coming Soon

- 🎥 **Video walkthroughs** — 15-minute video for each chapter
- 🎙️ **Audio episodes** — "The analytical question behind this chart" podcast
- 📝 **Exercises** — Build-it-yourself challenges at the end of each chapter
- 🏆 **Community showcase** — Best student charts featured in BarcaFutbol newsletter
- 🎓 **MOOC version** — Full structured course with assessments and certificate

---

## About BarcaFutbol and HackrLife

**BarcaFutbol** is an analytical football publication covering FC Barcelona
through data, tactics, and long-form writing. Available at
[barcafutbol.com](https://barcafutbol.com).

**HackrLife Media LLC** is a multi-property media company spanning football
analytics, AI/growth marketing, art crime, and financial analysis.
[hackrlife.com](https://hackrlife.com)

The Yamal vs Saka player comparison that this course is built around —
*"What Do You Get When You Pit Lamine Against Saka?"* — is available
at barcafutbol.com.

---

## Requirements

```
matplotlib>=3.8
scipy>=1.11
pandas>=2.0
numpy>=1.26
jupyter>=1.0
```

Install everything:
```bash
pip install matplotlib scipy pandas numpy jupyter
```

---

## Licence

Code: MIT — use it, adapt it, build on it.
Content and analysis: © 2026 HackrLife Media LLC / BarcaFutbol.
Data: © Sofascore.

---

*Built with Python, matplotlib, and the conviction that anyone can learn
to think analytically about football if you give them the right question.*

**[Start with Chapter 1 →](Chapter-01-The-Analytical-Question/)**
