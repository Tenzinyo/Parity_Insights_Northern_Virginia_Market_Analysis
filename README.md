# Northern Virginia Market Analysis

**Prepared by:** Parity Insights LLC
**Purpose:** Consultancy — Site Selection & Customer Profiling (Proven Data)
**Data Source:** U.S. Census Bureau, American Community Survey (ACS) 1-Year Estimates, 2025
**Scope:** Northern Virginia (NOVA) — Arlington, Fairfax, Fauquier, Loudoun, and Prince William Counties

---

## Overview

This repository contains a data-driven market analysis of Northern Virginia (NOVA) to support retail site selection and customer targeting decisions. The analysis is built on verified U.S. Census Bureau data and is structured around three core demographic pillars relevant to the client's target customer profile: **female population by age**, **household income by age cohort**, and **language diversity**.

The notebook `NOVA_market_analysis.ipynb` is the primary deliverable. It is designed to be reproducible and auditable, with all source data drawn directly from ACS public tables. All margin-of-error columns are excluded from analysis to keep the focus on point estimates.

---

## Repository Structure

```
Market Analysis/
├── NOVA_market_analysis.ipynb   # Main analysis notebook
├── README.md                    # This file
```

> **Note:** Raw CSV data files (ACS downloads) are loaded from `/content/` in the notebook, consistent with a Google Colab environment. To reproduce locally, update file paths in the data-loading cells accordingly.

---

## Analysis Sections

### 1. Female Population Demographics (Ages 20–59)

- **Data:** `ACSST1Y2025.S0101` — Age and Sex table
- **Goal:** Quantify the addressable female target market (ages 20–59) by county
- **Output:** Per-county pie charts showing age-band distribution of target females

**Counties analyzed:** Arlington, Fairfax, Prince William, Fauquier

**Key finding:** Fairfax County holds the largest absolute target-female population (~350K), with a balanced distribution across 35–49-year age bands — the highest-spend cohort.

---

### 2. Median Household Income by Age Group

- **Data:** `S1903` — Median Income in the Past 12 Months
- **Goal:** Identify income levels across householder age groups (15–24, 25–44, 45–64) to validate purchasing power in each county
- **Output:** Bubble matrix chart (county × age group, sized and colored by median income)

**Key finding:** The 25–44 cohort median income is highest in Loudoun ($206K) and Fairfax ($162K). Loudoun is excluded from the primary recommendation due to its dispersed, semi-rural geography and lower retail foot-traffic density. Fairfax represents the strongest combination of income depth and population scale.

---

### 3. Spoken Language Demographics

- **Data:** `S1602` — Language Spoken at Home
- **Goal:** Understand linguistic diversity to inform multilingual marketing and in-store experience strategy
- **Output:** Bubble matrix chart (county × language group, sized by household count)

**Key finding:** Fairfax has the highest absolute non-English speaking households — notably ~60K Asian/Pacific Island-language households and ~53K Spanish-speaking households. Multilingual outreach, particularly in Spanish and selected Asian languages, is advisable for any Fairfax location.

---

## Site Recommendation

Based on the three analyses combined, **Fairfax County** is the recommended market for expansion:

| Factor | Fairfax | Arlington | Prince William | Loudoun |
|---|---|---|---|---|
| Target female headcount (20–59) | Highest | High | High | High |
| Median income (25–44 cohort) | $162K | $127K | $145K | $206K |
| Geographic density / retail access | High | High | Medium | Low |
| Language diversity (marketing reach) | Very High | High | High | Medium |

Loudoun County, while income-leading, is geographically dispersed and not ideal given commute patterns and retail density considerations. Fairfax offers the deepest market with proven commercial infrastructure.

---

## Data Sources

| File | ACS Table | Description |
|---|---|---|
| `ACSST1Y2025.S0101-Data.csv` | S0101 | Age and sex by county |
| `income.S1903-Data.csv` | S1903 | Median household income by age |
| `spoken_language.S1602-Data.csv` | S1602 | Language spoken at home |

All data sourced from [data.census.gov](https://data.census.gov), ACS 1-Year Estimates, 2025.

---

## Dependencies

```
pandas
numpy
matplotlib
seaborn
```

Run in Google Colab or any Python 3.10+ environment with the above packages installed.

---

*Parity Insights LLC — Market Intelligence for Informed Decisions*
