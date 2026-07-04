# People Analytics Case Study - Recruitment Process Optimisation

Analysis of one year of recruitment data to help the Talent Acquisition team
understand process efficiency, identify funnel bottlenecks, and evaluate the
effectiveness of different sourcing channels.

> **Status:** In progress. The analysis runs on `applications_data.csv`, which is
> not versioned in this repository (see [Data](#data)).

---

## Context

The Head of Talent Acquisition is preparing for a quarterly business review and
needs to understand how efficient the recruitment process has been over the last
year, with a particular focus on two things: **where the process bottlenecks are**
and **which sourcing channels deliver the best return**.

This project takes a single candidate-level dataset, prepares it for analysis,
and turns it into a short, decision-oriented narrative for the Talent
Acquisition team.

---

## Business Questions

1. **Sourcing channel effectiveness** — Which channels deliver the best results,
   evaluated on both the *volume* of hires and the *efficiency* (conversion rate)
   of candidates from each source?
2. **Time to fill** — What is the average time to fill a role
   (`date_requisition_opened` → `date_hired`), and how does it differ across
   departments?
3. **Funnel health** — What are the conversion rates between the key stages of
   the hiring process, and where are the biggest drop-off points?
4. **Recommendations** — Based on the findings, what are the top 2–3 actionable
   recommendations to improve the process?

---

## Repository Structure

```
wise_people_analytics_case/
├── README.md                        # This file
├── requirements.txt                 # Python dependencies
├── .gitignore                       # Excludes venv, checkpoints, raw data
├── data/
│   ├── raw/                         # applications_data.csv (not versioned)
│   └── processed/                   # Prepared data, if persisted
├── notebooks/
│   └── recruitment_funnel_analysis.ipynb   # Main analysis, section by section
├── outputs/
│   └── figures/                     # Exported charts used in the presentation
└── docs/
    ├── case_brief.pdf               # Original case instructions
    └── presentation.pdf             # Final deliverable (up to 5 slides)
```

---

## Setup

The project uses a virtual environment to isolate dependencies.

```bash
# 1. Create and activate the environment
python3 -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Jupyter
jupyter lab
```

Then open `notebooks/recruitment_funnel_analysis.ipynb` and run the cells in order.

---

## Data

The analysis expects a single candidate-level file, `applications_data.csv`,
placed in `data/raw/`. **This file is intentionally not committed** — it contains
candidate-level personal data, so it is excluded via `.gitignore`.

Each row represents one candidate's application for a specific role.

| Column | Description |
| --- | --- |
| `application_id` | Unique identifier for each application |
| `candidate_id` | Unique identifier for each candidate |
| `job_id` | Unique identifier for the job requisition |
| `job_title` | e.g. "Data Scientist", "Sales Executive" |
| `department` | e.g. "Technology", "Sales", "Marketing" |
| `job_level` | e.g. "Associate", "Senior", "Manager" |
| `application_date` | Date the candidate applied |
| `source` | Channel the candidate applied through (LinkedIn, Employee Referral, Careers Site, Agency, University Job Board) |
| `current_stage` | The final stage the candidate reached in the process |
| `date_offer_extended` | Date an offer was made (blank if not applicable) |
| `date_hired` | Date the candidate was hired (blank if not applicable) |
| `date_requisition_opened` | Date the job was first opened |

---

## Approach

The notebook is organised to mirror the structure of the final presentation, so
the analysis reads top-to-bottom as a single narrative:

- **0. Setup & data loading** — imports, load the raw file, first look at shape,
  types, and missing values.
- **1. Data preparation** — parse dates, standardise categorical values, and
  reconstruct the recruitment funnel from the terminal-stage field so that stage
  counts are cumulative.
- **2. Sourcing channels** *(→ Slide 2)* — volume vs. conversion efficiency.
- **3. Funnel health** *(→ Slide 3)* — stage-to-stage conversion and drop-off
  points.
- **4. Time to fill** *(→ Slide 4)* — by department (mean and median).
- **5. Synthesis & recommendations** *(→ Slides 5 & 1)* — turning the numbers
  into actions.

A note on the funnel: `current_stage` records only the *furthest* stage each
candidate reached, so the number of candidates "entering" a given stage is
computed cumulatively (everyone whose furthest stage is that stage or later).

---

## Key Findings

_To be completed once the analysis is run._

1. …
2. …
3. …

---

## Deliverable

The final write-up (up to 5 slides) is available at
[`docs/presentation.pdf`](docs/presentation.pdf).

---

## Author

**Denerson** — [github.com/ddenerson](https://github.com/ddenerson)

Prepared as part of a People Analytics case study.
