# Chapter 1 — Tutorial Direction
## The Analytical Question

**Football Analytics with Python · BarcaFutbol Analytics Course**
**HackrLife Media LLC**

---

## What This Document Is

This is the instructor guide for Chapter 1. It explains:

- What the chapter is trying to achieve
- How each section connects to the next
- What a student should understand before moving on
- Common mistakes and how to address them
- How this chapter connects to the full 20-chapter arc

If you are a student working through the course independently,
this document gives you the reasoning behind every decision in the notebook.
Read it after completing the notebook for the deepest understanding.

---

## The Chapter in One Sentence

Chapter 1 teaches students that the question is more important than the chart —
and gives them their first chart to prove it.

---

## What Three Files Are Delivered

| File | What It Is | What To Do With It |
|------|-----------|-------------------|
| `Chapter_01_The_Analytical_Question.ipynb` | The Colab notebook | Open in Google Colab. Run every cell top to bottom. Read every text cell carefully. |
| `data/chapter01_players.csv` | Synthetic player data | Already loaded by the notebook. Edit it in Excel or a text editor for Exercise 3. |
| `TUTORIAL_DIRECTION.md` | This document | Read after completing the notebook for deeper context. |

---

## How to Open the Notebook

### Option 1 — Google Colab (Recommended)
1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Open notebook → GitHub**
3. Paste: `https://github.com/HackrLife/Football-Analytics`
4. Select `The-Football-Analytics-Course/Chapter-01.../Chapter_01_The_Analytical_Question.ipynb`
5. Click **File → Save a copy in Drive** — this gives you your own version to edit

### Option 2 — Download and Run Locally
1. Download the `.ipynb` file and the `data/` folder
2. Keep them in the same folder on your computer
3. Open a terminal and run: `jupyter notebook`
4. Navigate to the file and open it

### Option 3 — View Without Running
[View on nbviewer](https://nbviewer.org/github/HackrLife/Football-Analytics/blob/main/The-Football-Analytics-Course/Chapter-01-The-Analytical-Question/Chapter_01_The_Analytical_Question.ipynb) —
see all charts without running any code.

---

## Learning Objectives — In Plain English

By the end of this chapter, a student should be able to:

### 1. Explain the difference between descriptive and argumentative analysis

**Descriptive:** "Marcus scored 18 goals."
**Argumentative:** "Marcus scores above his expected rate — meaning he is a better
finisher than his shot selection suggests, and defenders who mark his runs are
underestimating his finishing ability."

A student who can write the argumentative version of three different football
statistics is ready for Chapter 2.

### 2. Explain why per-90 rates are more honest than raw totals

A player who scores 20 goals in 3,600 minutes is performing at the same rate as
one who scores 10 in 1,800 minutes. Raw totals reward availability. Per-90 rates
reward quality. Every statistical comparison in this course uses per-90 rates.

A student who can calculate a per-90 rate manually and explain why we use it
is ready for Chapter 2.

### 3. Load a CSV file into a pandas DataFrame and inspect it

```python
df = pd.read_csv('data/chapter01_players.csv')
df.head()
df.shape
df.describe()
```

These three operations — load, preview, summarise — are the first three things
any analyst does with new data. A student who can do them without looking at
the notebook is ready for Chapter 2.

### 4. Build a basic horizontal bar chart with the BarcaFutbol design system

The chart does not need to be perfect. It needs to have:
- Dark background
- Each player a different colour
- A readable title and axis label
- Value labels at the end of each bar

### 5. Read a scatter plot with arrows and explain what it shows

The scatter plot in this chapter shows two metrics simultaneously (goals and assists)
and uses arrows to show year-on-year change. A student who can look at that chart
and describe in words what happened to each player — without referring to the data
table — is ready for Chapter 2.

---

## Section by Section Breakdown

### Part 1 — Before We Touch Any Code
**What it teaches:** Analytical thinking. The difference between descriptions and insights.

**Why it comes first:** Most courses start with "here is how to install Python."
This course starts with "here is how to think." The code is easier than the thinking.
If a student skips Part 1 and goes straight to the code cells, they will be able
to build charts but unable to decide what charts to build. That is not analysis.

**Key idea to emphasise:**
A bad question produces a chart that shows you something.
A good question produces a chart that argues something.

**Test question for students:**
*"Take the statement 'Amir Hassan had 15 assists this season' and rewrite it
as an argumentative statement."*

A good answer might be: *"Amir Hassan creates more chances per 90 than any other
player in this group — which means he is the player most likely to unlock a deep
defensive block, and a team that struggles to break down low lines should be
looking at him."*

---

### Part 2 — Setting Up Python
**What it teaches:** Installing libraries. Importing tools. The design system.

**Why this order:** Environment setup is boring. We move through it quickly and
use it as an opportunity to introduce the colour palette — which is immediately
useful and gives the student something tangible from the setup section.

**Common mistake:** Students who skip the install cell and go straight to imports
will get `ModuleNotFoundError`. The fix is always: go back and run Cell 1 first.

**Key idea to emphasise:**
The design system is not decoration. Consistent colours across 8 charts signal
that the analysis was produced with intention, not assembled from random templates.
When a reader sees the same dark background and gold accent across every chart,
they trust the analysis more before reading a word.

**The palette naming convention:**
We name colours by what they *mean*, not what they *look like*.
`GREEN` does not mean "the colour green." It means "elite performance."
`RED` does not mean "the colour red." It means "below average performance."
This distinction matters when we build pizza charts in Chapter 8.

---

### Part 3 — Loading and Understanding Data
**What it teaches:** `pd.read_csv()`, `df.head()`, `df.describe()`, `df.pivot()`.
Per-90 rates. Data verification.

**Why verification comes here:**
The verification cell (Cell 4) is placed immediately after loading, before any
charting. This is intentional. The lesson is: verify before you visualise.
A wrong number in the data becomes a wrong chart. A wrong chart in a published
article is a credibility problem that cannot be undone.

**Key idea to emphasise:**
Always calculate at least one statistic by hand and compare it to the provided value.
In this case: `(goals / minutes_played) * 90` should equal `goals_per90`.
If it doesn't, the data has an error. If it does, you have confidence in the data.

**The synthetic data decision:**
The `chapter01_players.csv` data is fictional. This is deliberate for three reasons:
1. Students cannot be wrong about a fictional player's statistics
2. Fictional data can be designed to illustrate the concepts cleanly
3. Students are not distracted by prior knowledge of real players

From Chapter 2 onward, we work with real data. Chapter 1 is the safe space
to make mistakes before the stakes feel real.

**What the data is designed to show:**
- Marcus Silva: high goals, improving assists — the story of a finisher becoming a dual threat
- Lucas Ferreira: high assists, moderate goals — the pure creator archetype
- James Thornton: youngest player, biggest improvement — the development story
- Diego Varela: highest goals/90 in 23/24, near-flat in 24/25 — the plateau story
- Amir Hassan: most assists — the specialist creator who is now also scoring more
- Kai Becker: most balanced profile — moderate on everything, improving steadily

Each player represents a different football archetype. By the end of Chapter 9
(scatter plots), students will recognise these archetypes instinctively.

---

### Part 4 — Your First Chart (The Bar Chart, Three Steps)
**What it teaches:** `ax.barh()`, `fig.patch.set_facecolor()`, `ax.spines`,
`ax.grid()`, `ax.text()` for value labels, `ax.axvline()` for reference lines.

**Why three steps:**
Showing the chart go from ugly-but-correct to professional in two iterations
teaches a more important lesson than starting with the final version: the code
that makes a chart beautiful is small in volume but large in impact. Each of the
five design changes in Step 2 takes one line of code. Students who see this
understand that design is not difficult — it is just decisions.

**Step 1 purpose:** Prove the data is correct and the basic structure works.
**Step 2 purpose:** Apply the design system. Teach colour, background, spine removal.
**Step 3 purpose:** Add analytical context — value labels, average reference line, subtitle.

**The average reference line:**
`ax.axvline()` draws a vertical line at a specific value.
We use the gold colour from the design system (`color=GOLD`).
The purpose is not decorative. It answers the question: "above average or below?"
instantly, without the reader having to calculate anything.

**The subtitle:**
Every chart in this course has a two-line title: the metric and the analytical question.
`"Goals + Assists per 90 — 2024/25 Season\nWho is contributing most to their team's attack?"`
The first line is what. The second line is why. Both are necessary.

---

### Part 5 — The Scatter Plot
**What it teaches:** `ax.scatter()`, `ax.annotate()` with arrows, quadrant charts,
`ax.axvline()` and `ax.axhline()` for quadrant lines, legend construction.

**Why a scatter plot in Chapter 1:**
Chapter 1 is about the question, not the chart type. Scatter plots are covered
properly in Chapter 9. But we introduce one here because it perfectly illustrates
the difference between descriptive and argumentative analysis:

A bar chart shows one metric. It answers: "who scored the most?"
A scatter plot shows two metrics simultaneously. It answers: "what *type* of player
is each person, and in which direction are they developing?"

The scatter plot is more analytical by construction. Students who see this in
Chapter 1 understand from the beginning that chart choice is an analytical decision,
not an aesthetic one.

**The arrow technique:**
`ax.annotate()` with `arrowprops` draws an arrow between two points.
We use it to show year-on-year movement — the arrow tail is 23/24, the arrowhead is 24/25.
The direction and length of the arrow tells you more than either dot alone.

This technique appears again in Chapter 5 (career arc) and Chapter 14
(trajectory modelling). Students who understand it here will find those chapters easier.

**The quadrant labels:**
Dual Threat / Pure Finisher / Pure Creator / Limited Output.
These are not just labels on a chart. They are archetypes that appear throughout
football analytics. When a student can look at a scatter plot and immediately
identify which quadrant a player occupies, they are thinking like an analyst.

---

### Part 6 — Exercises
**What it teaches:** Modification, experimentation, independence.

**Philosophy:**
The exercises are not assessments. They are invitations to break things.
A student who changes the metric in Exercise 1 and produces a chart that
looks wrong has learned more than one who produces a chart that looks right
by copying the cell exactly.

**Exercise 1 (Easy):** Change one variable. Produces a working chart immediately.
Confidence builder. Should take 5 minutes.

**Exercise 2 (Medium):** Requires looking up `plt.subplots(1, 2)` or understanding
how to offset bar positions. Tests whether the student understands `figsize` and
the relationship between `fig` and `ax`. Should take 15–20 minutes.

**Exercise 3 (Hard):** Edit the CSV directly. Tests whether the student understands
that the data and the chart are separate — changing the data changes the chart.
Should take 30 minutes. Most students will discover something unexpected when they
add a new player. That discovery is the learning.

---

## Common Questions from Students

**Q: I got a FileNotFoundError when loading the CSV.**
A: The notebook looks for the data file at `'data/chapter01_players.csv'`.
Make sure the `data/` folder and the notebook are in the same directory.
In Colab, you need to upload the file or mount your Drive.

**Q: My chart background is white, not dark.**
A: You need to run Cell 2 (the design system cell) before Cell 6 (the chart cells).
The colour variables `BG`, `WHITE` etc. are defined in Cell 2.
If you skip it, Python does not know what `BG` means.

**Q: The arrows in the scatter plot are not showing.**
A: Check that your data has two rows per player (one per season).
The arrow is drawn between the two data points. If a player has only one row,
no arrow can be drawn. Check `df.groupby('player').size()` to confirm.

**Q: Can I use this code for real players?**
A: Yes. That is the point. Replace the CSV with real data, update the player
names in the `PLAYER_COLORS` dictionary, and every chart will rebuild automatically.
Chapter 2 teaches you how to collect and clean real data for exactly this purpose.

**Q: How do I save my chart as a PNG?**
A: Add this line before `plt.show()`:
```python
plt.savefig('my_chart.png', dpi=300, bbox_inches='tight', facecolor=BG)
```
`dpi=300` means high resolution — good for printing and newsletters.
`bbox_inches='tight'` removes extra white space around the chart.
`facecolor=BG` ensures the dark background is preserved in the saved file.

---

## How This Chapter Connects to the Course

| Chapter 1 introduces... | Which is used in... |
|-------------------------|---------------------|
| The design system (BG, WHITE, GOLD etc.) | Every chapter |
| `pd.read_csv()` and `df.head()` | Every chapter |
| `ax.barh()` | Chapter 6 (Bar Charts) |
| `ax.scatter()` with arrows | Chapter 9 (Scatter Plots), Chapter 14 (Trajectory) |
| `ax.axvline()` for reference lines | Chapter 8 (Pizza), Chapter 9 (Scatter), Chapter 13 (xG) |
| Per-90 rate calculation | Every chapter |
| The descriptive vs argumentative distinction | Every chapter |

Nothing in Chapter 1 is throwaway. Every concept introduced here reappears
in a more complex form later in the course.

---

## What to Check Before Moving to Chapter 2

A student is ready for Chapter 2 if they can answer yes to all of these:

- [ ] I can run all 9 code cells without errors
- [ ] I can explain what `df = pd.read_csv(...)` does in plain English
- [ ] I can explain what "per 90 minutes" means and why we use it
- [ ] I can look at the scatter plot and describe in words what happened to each player
- [ ] I completed at least Exercise 1 successfully
- [ ] I understand the difference between a descriptive and argumentative statement
      about a football statistic

If any of these are incomplete, re-read the relevant section of the notebook
before proceeding. Chapter 2 assumes all of Chapter 1.

---

## Video and Audio Companion (Coming Soon)

**Video walkthrough (15 min):**
A screen recording of the notebook being run live, with spoken commentary
explaining every decision — including the ones that are not in the code,
like why we chose a horizontal bar chart instead of a vertical one,
and why the quadrant labels matter.

**Audio episode (10 min):**
"The Analytical Question" — a standalone podcast episode on why most football
analytics is descriptive and what it takes to make it argumentative instead.
No code. No charts. Just the thinking. Accessible to anyone, including those
who have not started the course yet.

Both available at [barcafutbol.com](https://barcafutbol.com) and wherever
you listen to podcasts.

---

## A Note on Pace

This course is not a race. Chapter 1 is deliberately slower than the chapters
that follow. If you spend two hours on Chapter 1 and understand everything in
it deeply, you will spend 30 minutes on Chapter 6 because the foundations are solid.

If you rush Chapter 1 and move to Chapter 2 without understanding per-90 rates
and the difference between descriptive and argumentative analysis, every chapter
after it will be harder than it needs to be.

**Take your time here. It is worth it.**

---

*© 2026 HackrLife Media LLC / BarcaFutbol Analytics Course*
*[github.com/HackrLife/Football-Analytics](https://github.com/HackrLife/Football-Analytics)*
*Full article this course is built around: [barcafutbol.com](https://barcafutbol.com)*
