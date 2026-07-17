# Recruitment Process Analysis - People Analytics Case Study

A People Analytics case study analysing one year of recruitment data to help a
Talent Acquisition team understand process efficiency, identify funnel
bottlenecks, and evaluate the effectiveness of their sourcing channels.

> **Context:** This was a take-home case study for a **Senior Data Analyst -
> People Analytics** role at **Wise**. It is shared here as a portfolio piece.


---

## The Brief

The Head of Talent Acquisition was preparing for a quarterly business review and
needed to understand how efficient the recruitment process had been over the past
year, with a focus on two things: **where the process bottlenecks are** and
**which sourcing channels deliver the best return**.

The task was to turn a single candidate-level dataset into a short, decision-ready
story - delivered as a 5-slide presentation, backed by a reproducible analysis.

## Business Questions

1. **Sourcing channel effectiveness** — which channels perform best on *volume* of
   hires and *efficiency* (conversion rate)?
2. **Time to fill** — average time from requisition opened to hire, and how it
   varies by department.
3. **Funnel health** — conversion rates between hiring stages, and where the
   biggest drop-offs happen.
4. **Recommendations** — the top actions to improve the process.

---

## Key Findings

**The interview process works — the problem is the entrance.** Once a candidate
passes the first screen, the funnel converts above 86% at every stage and hiring
takes about 40 days, uniform across all departments. The losses happen earlier.

1. **The first screen is the real bottleneck.** 82% of all funnel losses happen at
   the Applied to HR Screen step (only 41% pass). Every later stage is healthy.
2. **Sourcing is misallocated.** LinkedIn drives most hires, but Employee Referral
   converts 2.7x better on low volume — while three channels (Agency, Indeed,
   University Job Board) produced zero hires from 121 applications.
3. **The funnel has a blind spot.** 55% of candidates have no recorded exit stage,
   so the true drop-off points can't be fully measured — a data quality gap that
   is itself a finding.
4. **The official time-to-fill metric is unreliable**, distorted by a data
   artifact in the dates; time to hire is used as the trustworthy measure instead.

---

## Approach

The notebook is organised to mirror the final presentation, so it reads
top-to-bottom as a single narrative:

- **0. Setup & data loading** — load the raw file, first look at shape, types, and
  missing values.
- **1. Data preparation** — parse dates, handle data quality issues, and
  reconstruct the funnel from the terminal-stage field so stage counts are
  cumulative.
- **2. Sourcing channels** — volume vs. conversion efficiency.
- **3. Funnel health** — stage-to-stage conversion and drop-off points.
- **4. Time to fill** — by department, with a caveat on the distorted metric.
- **5. Synthesis & recommendations** — turning the numbers into actions.

Every figure in the presentation traces back to a specific cell in the notebook.

---

## Repository Structure

```
wise-people-analytics-case/
├── README.md
├── requirements.txt
├── docs/
│   ├── case_brief.pdf          # Original case instructions
│   └── presentation.pdf        # Final deliverable (5 slides)
├── data/
│   ├── raw/                    # applications_data.csv (not versioned)
│   └── processed/
├── notebooks/
│   └── recruitment_funnel_analysis.ipynb
└── outputs/
    └── figures/                # Exported charts
```

## Setup

```bash
python3 -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

Then open `notebooks/recruitment_funnel_analysis.ipynb` and run the cells in order.

## Data

The analysis expects a candidate-level file, `applications_data.csv`, in
`data/raw/`. It is **not committed**, as it contained candidate personal data.
Each row represented one candidate's application for a role, with fields for the
job, department, source channel, current stage, and key dates (application, offer,
hire, requisition opened).

---

## Tools

Python (pandas), Matplotlib / Seaborn, Jupyter, Git.

## Author

**Denerson Silva** — [github.com/ddenerson](https://github.com/ddenerson)
