# Census Data Analysis — Demographic Profiling & Strategic Planning for a UK Commuter Town

---

## What this project does

This notebook analyses a simulated UK census dataset to produce evidence-based recommendations for town planning and infrastructure investment. The work covers the full data science workflow: loading, cleaning, feature engineering, visualisation, and interpretation.

The two central questions driving the analysis:
1. **What should be built on an unoccupied plot of land?**
2. **Which area should receive priority investment?**

The answers are data-driven — every recommendation is backed by visualisations and demographic evidence from the census.

---

## Dataset

**File:** `T2_A24_census5.xlsx`
**Size:** 9,913 individual resident records, 11 attributes

Key columns include: House Number, Street, Age, Gender, Marital Status, Relationship to Head of House, Occupation, Infirmity, Religion.

---

## Data cleaning

The raw dataset had inconsistencies across multiple columns. Each was handled systematically:

| Column | Issue | Fix Applied |
|--------|-------|-------------|
| Marital Status | Missing for adults, present for children | Set to `N/A` for under-18s, filled adult nulls as `Single` |
| Relationship to Head of House | Blank strings, `nan`, `None` | Standardised to `Unknown` |
| Infirmity | Mixed placeholders and real values | Replaced all non-informative entries with `None` |
| Religion | Inconsistent casing, rare entries | Title-cased, `Atheist` → `No Religion`, grouped rare religions (<20 people) as `Other/Unknown` |
| Gender | Inconsistent capitalisation | Standardised to `Male` / `Female` |
| Age | Needed type casting | Validated range (0–110), cast to `int` |

Following cleaning, the dataset achieved **98%+ completeness** across all critical columns. Cross-tabulation confirmed no illogical combinations remained (e.g. no children flagged as divorced).

---

## Feature engineering

Three derived columns were created to support downstream analysis:

- **`Household`** — unique identifier combining House Number + Street (e.g. `12_High Street`)
- **`Household Occupancy`** — count of individuals per household
- **`age_group`** — 12 custom bins from `0-4` through `90+`
- **`OccCategory`** — occupation categorised as: Professional, Student, Retired, Unemployed, Child, Other
- **`LikelyCommuter`** — boolean flag for adults in professional/student roles with no local university

---

## Analysis & visualisations

| Plot | Purpose |
|------|---------|
| Age Distribution Histogram | Overview of population age structure |
| Population Age Pyramid | Male/female balance across age bands |
| Marital Status Heatmap by Age Group | When marriage patterns emerge |
| Relationship Type Bar Chart | Household composition |
| Infirmity Distribution | Common health conditions (excluding None) |
| Religion Distribution | Assess religious facility demand |
| Religion Trends by Age Band | Whether minority religions are growing |
| Median Age by Religion | Demographic composition per faith group |
| Occupation Category Breakdown | Workforce composition |
| Commuter Population (Pie) | Proportion of residents commuting out |
| Unemployment by Age & Gender | Which groups are most affected |
| Household Occupancy by Marital Status | Living arrangement patterns |
| Birth Rate Indicator (Ages 0–4) | Estimate future school demand |
| Ageing Indicator (Ages 80+) | Estimate future elderly care demand |
| Divorce Rate by Gender | Social and housing implications |

---

## Key findings

**Population structure:** The town has a broad working-age base (20–59), with moderate ageing and a declining birth rate. No demographic crisis — but gradual elderly care demand is building.

**Commuting:** Nearly 50% of employed adults are likely commuters. All university students commute daily since the town has no local university. Commuting defines the town's identity.

**Unemployment:** ~10% of working-age adults are unemployed — above the UK average. Highest concentration is in the 20–35 age group, suggesting a skills mismatch rather than a general labour shortage.

**Religion:** Christianity and No Religion dominate. Minority religions have limited and stable representation — no justification for new religious infrastructure.

**Household structure:** Married residents live in larger households. Widowed residents predominantly live alone. Divorced females outnumber divorced males, suggesting women stay in the community post-separation.

---

## Recommendations

**What to build:** A **train station**. With ~50% of employed adults commuting and all university students travelling out daily, transport connectivity is the single biggest lever for quality of life and economic growth.

**Where to invest:** **Employment and skills training**. Youth unemployment (20–35) is the most structurally significant problem — it affects long-term earnings, civic participation, and economic resilience. A train station without skills investment solves access but not opportunity.

Full reasoning and supporting figures are in the accompanying report.

---

## Report

A full written report (`Azeez_Abdul-Majeed_Census_Report.pdf`) accompanies this notebook. It includes extended interpretation of each finding, policy implications, and references to comparable UK case studies.

---

## How to run

```bash
# Clone the repo
git clone https://github.com/Meezxbt2001/census-data-analysis.git
cd census-data-analysis

# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook Final_Project.ipynb
```

Place `T2_A24_census5.xlsx` in the same directory as the notebook before running.

---

## Requirements

```
numpy
pandas
matplotlib
seaborn
openpyxl
jupyter
```

---

## Project structure

```
census-data-analysis/
│
├── Final_Project.ipynb                      # Main analysis notebook
├── Azeez_Abdul-Majeed_Census_Report.pdf     # Full written report
├── requirements.txt
└── README.md
```

---

## References

- Office for National Statistics (2021) *Census 2021 — Methods and Quality Report*. ONS.
- McKinney, W. (2017) *Python for Data Analysis*. 2nd edn. O'Reilly Media.
- Waskom, M. (2021) Seaborn: Statistical Data Visualization. *Journal of Open Source Software*, 6(60), p. 3021.
- HM Government (2022) *Levelling Up the United Kingdom*. Department for Levelling Up, Housing and Communities.

---

## Author

**Azeez Abdul-Majeed Babatunde**
MSc Artificial Intelligence & Data Science
University of Hull
