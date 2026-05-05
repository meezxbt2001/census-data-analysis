# Census Data Analysis

A data analysis and demographic profiling project completed as part of the **MSc Artificial Intelligence & Data Science** programme at the **University of Hull**.

The project analyses a historical census dataset to produce evidence-based recommendations for town planning, infrastructure investment, and community services.

---

## Overview

Using a census Excel dataset (`T2_A24_census5.xlsx`), this project performs end-to-end data wrangling, cleaning, exploratory analysis, and visualisation to answer key demographic and planning questions about a fictional town.

---

## Project Structure

```
├── Final_Project.ipynb     # Main analysis notebook
└── README.md
```

> **Note:** The source dataset (`T2_A24_census5.xlsx`) is not included as it was provided as part of coursework.

---

## What the Notebook Covers

### 1. Data Loading & Inspection
- Loaded census data from Excel using `pandas`
- Identified missing values across key columns: Surname, Relationship to Head of House, Infirmity, Religion, Marital Status

### 2. Data Cleaning
Each column was cleaned systematically:

| Column | Cleaning Applied |
|--------|-----------------|
| Age | Validated range (0–110), cast to `int`, detected outliers |
| Marital Status | Set to `N/A` for under-18s, filled missing adult entries as `Single` |
| Relationship to Head of House | Replaced blanks/nulls with `Unknown`, standardised formatting |
| Infirmity | Unified `No Infirmity` / `none` → `None`, replaced placeholders with `NaN` |
| Religion | Title-cased, replaced `Atheist` → `No Religion`, grouped rare religions (<20 people) as `Other/Unknown` |
| Occupation | Categorised into: Professional, Student, Retired, Unemployed, Child, Other |
| Gender | Standardised capitalisation |

### 3. Feature Engineering
- Created a unique `Household` identifier by combining House Number and Street
- Derived `age_group` column with 12 custom age bands
- Computed `Household Occupancy` per household
- Created `OccCategory` (occupation category) and `LikelyCommuter` flag

### 4. Exploratory Data Analysis & Visualisations

| Plot | Purpose |
|------|---------|
| Age Distribution Histogram | Overview of population age structure |
| Marital Status Heatmap by Age Group | Identify when marriage is most common |
| Relationship Type Bar Chart | Describe household composition |
| Infirmity Distribution | Identify common health conditions |
| Religion Distribution + Age Trends | Assess religious facility demand |
| Population Age Pyramid | Assess ageing vs youth balance |
| Occupation Category Breakdown | Understand workforce composition |
| Commuter Population | Justify transport infrastructure investment |
| Unemployment by Age & Gender | Identify groups needing employment support |
| Household Occupancy Distribution | Identify overcrowding |
| Birth Rate Indicator (Ages 0–4) | Estimate future school demand |
| Death Rate Indicator (Ages 80+) | Estimate elderly care demand |
| Divorce Rate by Gender | Assess social and housing implications |
| Median Age by Religion | Understand demographic composition per faith group |
| Household Occupancy by Marital Status & Age | Understand living arrangements |

### 5. Summary Metrics Table
A final summary DataFrame was produced covering:
- Total population and households
- Average household occupancy
- Unemployment rate (ages 18–65)
- Birth rate per 1,000
- Commuter proportion
- Religious breakdown (%)
- Infirmity/disability rate
- Near-retirement and elderly population counts

---

## Tools & Libraries

| Library | Usage |
|---------|-------|
| `pandas` | Data loading, cleaning, grouping, feature engineering |
| `numpy` | Numerical operations, histogram binning |
| `seaborn` | Statistical visualisations |
| `matplotlib` | Plot customisation and saving |

---

## Key Findings

- The town has a noticeably **ageing population**, with significant counts in the 60–80+ age bands
- A high proportion of **likely commuters** (professionals and university students) supports the case for improved public transport
- **Divorced females outnumber divorced males**, suggesting female-led single-parent households are prevalent
- **Christianity and No Religion** are the dominant categories, limiting immediate demand for new religious infrastructure
- A relatively **low birth rate** reduces near-term school expansion pressure, but healthcare and elderly care investment appears justified

---

## Author

**Azeez Abdul-Majeed Babatunde**  
MSc Artificial Intelligence & Data Science  
University of Hull
