# State-Level Wage Analysis: US Electricians, 2023-2025

## 1. Abstract
The US is facing a well-documented shortage of skilled tradespeople. The BLS projects 9% growth in electrician employment from 2024 to 2034, alongside roughly 81,000 annual openings, and the National Electrical Contractors Association (NECA) reports that close to 30% of union electricians are nearing retirement age. Yet it remains unclear whether wages are rising fast enough to attract new workers into the trade at the pace demand requires. This project uses BLS OEWS data from 2023 to 2025, across 50 states, to examine whether electrician wages show signs of stagnation or growing inequality, one possible lens on why the labor gap persists despite rising demand.

## 2. Data Source
* Bureau of Labor Statistics: OEWS
* Years covered: 2023, 2024, 2025
* 50 states (DC excluded along with Puerto Rico, Guam and US Virgin Islands)

## 3. Data Cleaning
* Raw exports: one table per year, extracted from BLS OEWS.
* Filtered each table to only include occupation: "Electricians" and to exclude DC, Puerto Rico, Guam and US Virgin Islands from the States Column.
* Removed unnecessary columns e.g. Area Code, Area Type and Industry Type.
* Standardized column headers across all three years (resolved naming inconsistencies, e.g. "Ratio of Top vs Bottom 10% Earners" vs "Top vs Bottom 10% Earners").
* Verified no missing values or duplicate states across all 3 years.
* Added data reliability layer: flagged % error columns (employment, wage) into Low/Moderate/High bands, thresholds calibrated to this dataset's actual error distribution (employment >8%, wage >4%).
* Combined per-state error bands into a single "Flag" column (OK / Use with caution) for filtering and visual flagging


## Calculated Metrics
* **Avg-Median Gap (% of Median)** — `(Average − Median) / Median`, a proxy for wage distribution skew
* **Ratio of Top 10% to Bottom 10%** — `Top10 / Bottom10`, normalized inequality measure
* **% Change (Total, per period)** — `(End − Start) / Start`, calculated for avg, median, top10, bottom10 wages, employment, and density
* **CAGR** — `(End/Start)^(1/n) − 1`, smoothed annual growth rate
* **Avg-Median Growth Delta** — `Median growth % − Average growth %`, whether skew is widening (negative) or narrowing (positive) over time
* **Correlations** — Pearson r via `CORREL()`, tested for density-vs-wages, employment-vs-wages, and employment-growth-vs-skew-delta, each with a sensitivity check excluding Vermont
