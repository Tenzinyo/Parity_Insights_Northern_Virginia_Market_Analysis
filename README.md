# Northern Virginia Market Analysis

**Prepared by:** Parity Insights LLC
**Purpose:** Consultancy — Site Selection & Customer Profiling (Proven Data)
**Data Source:** U.S. Census Bureau, American Community Survey (ACS) 1-Year Estimates (2025) & 5-Year Estimates (2024)
**Scope:** Northern Virginia (NOVA) — Arlington, Fairfax, Fauquier, Loudoun, and Prince William Counties

---

## Overview

This repository contains a data-driven market analysis of Northern Virginia (NOVA) to support retail site selection and customer targeting decisions. The analysis is built on verified U.S. Census Bureau data and is structured in two phases:

1. **County-level analysis** across all five NOVA jurisdictions using ACS 1-Year 2025 estimates
2. **Census tract-level drill-down** into Fairfax County using ACS 5-Year 2024 estimates and geospatial shapefiles

The notebook `NOVA_market_analysis.ipynb` is the primary deliverable. It is designed to be reproducible and auditable, with all source data drawn directly from ACS public tables. All margin-of-error columns are excluded from analysis to keep the focus on point estimates.

**Research Questions Addressed:**
- What are the gender dynamics in NOVA?
- What are the income dynamics across age cohorts?
- What are the language and cultural demographics?
- Which specific Fairfax County towns offer the strongest retail opportunity?

---

## Repository Structure

```
Market Analysis/
├── NOVA_market_analysis.ipynb              # Main analysis notebook
├── README.md                               # This file
├── ACSST1Y2025.S0101-Data.csv             # County-level age & sex (ACS 1-Year 2025)
├── ACSST1Y2025.S1903-Data.csv             # County-level median household income (ACS 1-Year 2025)
├── ACSST1Y2025.S1602-Data.csv             # County-level language spoken at home (ACS 1-Year 2025)
├── ACSST1Y2025.S2401-Data.csv             # County-level occupation data (ACS 1-Year 2025)
├── ACSST1Y2025.S2403-Data.csv             # County-level industry data (ACS 1-Year 2025)
├── ACSST5Y2024.S0101-Data.csv             # Census tract age & sex (ACS 5-Year 2024)
├── ACSST5Y2024.S1903-Data.csv             # Census tract median household income (ACS 5-Year 2024)
├── ACSST5Y2024.S0802-Data.csv             # Census tract commute patterns (ACS 5-Year 2024)
└── Fairfax_County_Boundary_*/             # Fairfax County boundary shapefile (Esri)
    ├── Fairfax_County_Boundary.shp
    └── ...
```

> **Note:** Raw CSV data files (ACS downloads) are loaded from `/content/` in the notebook, consistent with a Google Colab environment. Virginia census tract shapefiles are downloaded at runtime from the U.S. Census Bureau TIGER/Line server. To reproduce locally, update file paths in the data-loading cells accordingly.

---

## Analysis Sections

### 1. Female Population Demographics — County Level (Ages 20–59)

- **Data:** `ACSST1Y2025.S0101` — Age and Sex table (ACS 1-Year 2025)
- **Goal:** Quantify the addressable female target market (ages 20–59) by county
- **Output:** Per-county pie charts showing age-band distribution of target females

**Counties analyzed:** Arlington, Fairfax, Prince William, Fauquier

| County | Key Finding |
|---|---|
| **Arlington** | Heavily skewed toward young professionals. Ages 25–29 = 25.5%, Ages 30–34 = 18.9%. Combined 25–34 cohort = **44.4%** of target females. |
| **Fairfax** | Highly balanced and mature distribution. Largest segments: 40–44 (13.7%), 25–29 (12.3%), 30–34 (12.1%). Stable long-term retail base. |
| **Prince William** | Steady distribution, strength in 40–44 (13.5%) and 30–34 (11.1%). Family-oriented suburban demographic. |
| **Fauquier** | Older skew — 40–44 (15.5%), 50–54 (14.2%). **41.3%** of target females are aged 45+. Mature, high-net-worth suburban households. |

---

### 2. Median Household Income by Age Group — County Level

- **Data:** `ACSST1Y2025.S1903` — Median Income in the Past 12 Months (ACS 1-Year 2025)
- **Goal:** Identify income levels across householder age groups (15–24, 25–44, 45–64) to validate purchasing power
- **Output:** Bubble matrix chart (county × age group, sized and colored by median income)

| County | 15–24 yrs | 25–44 yrs | 45–64 yrs |
|---|---|---|---|
| Arlington | $70,967 | — | $203,754 |
| Fairfax | $71,756 | $161,948 | — |
| Fauquier | $118,590 | — | — |
| Loudoun | $52,997 | — | $215,139 |
| Prince William | $87,145 | — | — |

**Key finding:** Median household income rises sharply with age across all jurisdictions. Loudoun leads at peak ($215,139 for ages 45–64) and Arlington follows ($203,754). Fairfax is highly competitive at $161,948 for the primary 25–44 target cohort, matched with the highest population density in NOVA.

---

### 3. Spoken Language Demographics — County Level

- **Data:** `ACSST1Y2025.S1602` — Language Spoken at Home (ACS 1-Year 2025)
- **Goal:** Understand linguistic diversity to inform multilingual marketing and in-store experience strategy
- **Output:** Bubble matrix chart (county × language group, sized by household count)

**Key finding:** Fairfax has the highest absolute non-English speaking households — **60,213** Asian and Pacific Island-language households and **53,066** Spanish-speaking households. Prince William is second in Spanish speakers (32,644). Multilingual outreach in Spanish and selected Asian languages is strongly advisable for any Fairfax or Prince William location.

---

### 4. Fairfax County Census Tract Analysis

With Fairfax identified as the primary target market, the analysis drills down to census tract level using ACS 5-Year 2024 data and geospatial shapefiles to pinpoint the optimal town for a second location.

**Data:** `ACSST5Y2024.S0101`, `ACSST5Y2024.S1903`, Virginia TIGER/Line census tract shapefiles (2024)
**Scope:** 84 census tracts merged across Fairfax County
**Towns analyzed:** Reston, Herndon, Tysons, Vienna, McLean, Annandale, Springfield, Centreville, Chantilly, Burke

#### 4a. Age Demographics Heatmap (Ages 15–64)

- **Output:** Choropleth heatmap of Fairfax County census tracts (YlOrRd color scale) overlaid on USGS Topo basemap, with 10 key town labels annotated
- **Total target population (ages 15–64) across 84 merged tracts:** 221,184
- **Key finding:** Vienna, Herndon, and Reston show the highest concentrations of the target-aged population. Vienna stands out for its central positioning between other populous areas, making it strategically accessible from multiple high-density corridors.

#### 4b. Target Population by Town — Bar Chart

- **Output:** Horizontal bar chart ranking 10 towns by total target-age population (15–64), color-coded using viridis palette
- **Key finding:** Vienna ranks #1 in total 15–64 population among Fairfax towns. Tysons follows closely and is in direct proximity to Vienna — a business accessible to both would capture a combined high-density consumer base.

#### 4c. Income Heatmaps by Age Group — 3-Panel Map

- **Output:** Three side-by-side choropleth maps (YlGnBu scale) showing median household income per census tract for householders aged 15–24, 25–44, and 45–64
- **Total income coverage:** 17,967,737 (sum of median income estimates across 84 tracts)
- **Key finding:** Income levels are geographically differentiated — eastern Fairfax tracts near McLean and Tysons show strong 25–44 income, while southern/western tracts around Burke and Centreville lead in 45–64 earnings.

#### 4d. Income by Town — Grouped Bar Chart

- **Output:** Grouped bar chart showing average median household income per town across all three age brackets
- **Key findings:**
  - **Burke and Centreville** lead for Ages 45–64, both exceeding **$137,000** — optimal for premium or luxury brands targeting established households
  - **Reston and Tysons** show strong entry-level income for Ages 15–24, and high mid-career earning for 25–44 — ideal for trendy, high-growth retail brands
  - Ages 25–44 income is consistently **$80,000–$110,000** across nearly all towns

---

## Site Recommendation

Based on the combined county-level and census tract analyses, **Fairfax County** is the confirmed primary market, with **Vienna** as the top candidate for a second location.

### County-Level Comparison

| Factor | Fairfax | Arlington | Prince William | Loudoun |
|---|---|---|---|---|
| Target female headcount (20–59) | Highest | High | High | High |
| Median income (25–44 cohort) | $162K | $127K | $145K | $206K |
| Geographic density / retail access | High | High | Medium | Low |
| Language diversity (marketing reach) | Very High | High | High | Medium |

Loudoun County, while income-leading, is geographically dispersed and not ideal given commute patterns and retail density considerations. Fairfax offers the deepest market with proven commercial infrastructure.

### Town-Level Recommendation within Fairfax

| Town | Strength | Best For |
|---|---|---|
| **Vienna** | Highest target-age pop, central location | Primary recommendation — broad demographic reach |
| **Tysons** | Adjacent to Vienna, strong youth/mid income | High foot-traffic retail, accessible from Vienna |
| **Reston** | High target-age pop, strong young professional income | Trendy brands, tech-adjacent workforce |
| **Burke / Centreville** | Peak 45–64 income (>$137K) | Premium/luxury services targeting established households |

**Vienna is the top recommendation** due to its combination of the highest 15–64 population concentration among Fairfax towns, centrally located between Tysons, Reston, and McLean, and balanced age and income diversity that reduces reliance on a single demographic cohort.

---

## Data Sources

| File | ACS Table | Description | Geography Level |
|---|---|---|---|
| `ACSST1Y2025.S0101-Data.csv` | S0101 | Age and sex by county | County (1-Year 2025) |
| `ACSST1Y2025.S1903-Data.csv` | S1903 | Median household income by age | County (1-Year 2025) |
| `ACSST1Y2025.S1602-Data.csv` | S1602 | Language spoken at home | County (1-Year 2025) |
| `ACSST1Y2025.S2401-Data.csv` | S2401 | Occupation by sex | County (1-Year 2025) |
| `ACSST1Y2025.S2403-Data.csv` | S2403 | Industry by sex | County (1-Year 2025) |
| `ACSST5Y2024.S0101-Data.csv` | S0101 | Age and sex by census tract | Tract (5-Year 2024) |
| `ACSST5Y2024.S1903-Data.csv` | S1903 | Median household income by age | Tract (5-Year 2024) |
| `ACSST5Y2024.S0802-Data.csv` | S0802 | Commute patterns | Tract (5-Year 2024) |
| `Fairfax_County_Boundary.shp` | — | Fairfax County boundary shapefile | County (Esri, 2026) |
| `tl_2024_51_tract.zip` | — | Virginia census tract boundaries | State/Tract (TIGER 2024) |

All ACS data sourced from [data.census.gov](https://data.census.gov). Virginia TIGER/Line shapefile downloaded from the U.S. Census Bureau at runtime.

---

## Dependencies

```
pandas
numpy
matplotlib
seaborn
geopandas
contextily
pyproj
shapely
```

Run in Google Colab or any Python 3.10+ environment with the above packages installed.

---

*Parity Insights LLC — Market Intelligence for Informed Decisions*
