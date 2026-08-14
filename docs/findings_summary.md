# State-Level Wage Analysis: US Electricians, 2023-2025

## Abstract
The US is facing a well-documented shortage of skilled tradespeople. The BLS projects 9% growth in electrician employment from 2024 to 2034, alongside roughly 81,000 annual openings, and the National Electrical Contractors Association (NECA) reports that close to 30% of union electricians are nearing retirement age. Yet it remains unclear whether wages are rising fast enough to attract new workers into the trade at the pace demand requires. This project uses BLS OEWS data from 2023 to 2025, across 50 states, to examine whether electrician wages show signs of stagnation or growing inequality, one possible lens on why the labor gap persists despite rising demand.

## Data Source
* Bureau of Labor Statistics: OEWS
* Years covered: 2023, 2024, 2025
* 50 states (DC excluded along with Puerto Rico, Guam and US Virgin Islands)

## Data Cleaning
* Raw exports: one table per year, extracted from BLS OEWS.
* Filtered each table to only include occupation: "Electricians" and to exclude DC, Puerto Rico, Guam and US Virgin Islands from the States Column.
* Removed unnecessary columns e.g. Area Code, Area Type and Industry Type.
* Standardized column headers across all three years (resolved naming inconsistencies, e.g. "Ratio of Top vs Bottom 10% Earners" vs "Top vs Bottom 10% Earners").
* Verified no missing values or duplicate states across all 3 years.
* Added data reliability layer: flagged % error columns (employment, wage) into Low/Moderate/High bands, thresholds calibrated to this dataset's actual error distribution (employment >8%, wage >4%).
* Combined per-state error bands into a single "Flag" column (OK / Use with caution) for filtering and visual flagging


## Calculated Metrics
* **Avg-Median Gap (% of Median)** — `(Average − Median) / Median`, an approximation for wage distribution skew, based on the principle that average and median are equal in a perfectly symmetric distribution, so the size of the gap between them indicates the degree of skew.
* **Ratio of Top 10% to Bottom 10%** — `Top10 / Bottom10`, normalized inequality measure
* **% Change (Total, per period)** — `(End − Start) / Start`, calculated for avg, median, top10, bottom10 wages, employment, and density - A normalized measure of change over time, expressed relative to the starting value so that growth can be fairly compared across states with different baseline wage or employment levels.
* **CAGR** — `(End/Start)^(1/n) − 1`, compound annual growth rate - converts the total 2023 to 2025 change into a single steady annual growth rate (accounted for compounding), rather than simply averaging the year-over-year percentages together.
* **Avg-Median Growth Delta** — `Median growth % − Average growth %`, if average wages are growing faster than median wages then skew is widening (negative) and in the opposite case the skew is narrowing (positive) over time.
* **Correlations** — Pearson r via `CORREL()`, tested for density-vs-wages, employment-vs-wages, and employment-growth-vs-skew-delta, each with a sensitivity check excluding Vermont

## Research Questions
* Which 10 states pay electricians the highest avg. hourly wage in 2023, 2024 and 2025 + lowest 10?
* How does the average vs median wage compare per state?
* Which states have the widest spread between bottom 10% and top 10% wage earners?
* Which states saw the largest % increase in avg. hourly wage over the three years?
* Is wage growth consistent across percentiles, or are top earners (90th percentile) growing faster than bottom earners (10th percentile) in certain states?
* Which states have the highest electrician density (electricians per 1,000 jobs)? Does higher density correlate with lower or higher wages (supply/demand effect)?
* Which states have the largest total employment growth 2023-2025, and does that align with wage growth or dilute it?

## Methodology
All figures below are drawn from BLS OEWS state-level estimates. Each estimate carries a published margin of error for both employment and wage figures. States with error bands flagged "High" in either metric (thresholds calibrated to this dataset: employment error >8%, wage error >4%) are noted individually and treated with caution rather than excluded outright. Where a finding depends on a flagged state, a sensitivity check (recalculating with that state removed) was run to confirm the result holds.
A small number of state-year estimates carry notably higher margins of error than the rest of the dataset, most consistently Vermont (2025 wage error: 7.4%, up from 0.8% in 2024) and Maine (2025 employment error: 9.1%), both small-workforce states where BLS sampling produces less stable percentile estimates. These states are flagged throughout, and any headline ranking they appear in is noted accordingly.
Vermont was tested as a sensitivity case across every correlation and ranking in this analysis, given its flagged reliability status and its consistent appearance as a statistical outlier. In each case, excluding Vermont changed the result only modestly, confirming the overall patterns are not artifacts of a single unreliable data point.

## Findings
1. **[Where Pay Stands](https://public.tableau.com/views/WageStatistics-WherePayStands/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**
* Average hourly wage increased for nearly every state between 2023 to 2025 - some exceptions were North Dakota, Iowa, Massachusetts, New Mexico, New York, Mississippi and California where wages either declined or stayed relatively stagnant.
  
* For Avg-Median Wage Gap, the highest single gap recorded across the three years was Vermont in 2025, at 15.7% of median, though this coincides with Vermont's flagged reliability issue that year and should be read cautiously. Excluding Vermont, the next-highest gap was New Jersey in 2023, at 15.1% of median. Looking across all states, the maximum gap recorded in any given year has trended downward from 2023 to 2025, though there were variations at the individual state level, some states' wage gaps widened over the period while others narrowed.
  
* The ratio of Top 10% wage earners vs Bottom 10% wage earners was calculated to measure how much more the Top 10% are making - New Jersey had the highest ratio in 2024 with the Top 10% making 3.36x the Bottom 10% electricians, California followed in 2025 with the Top 10% making 2.99x the Bottom 10%. Overall, 25 states showed this ratio on a declining trend from 2023-2025, suggesting the gap between Top 10% wages and Bottom 10% wages was reducing, while the other 25 states showed the opposite trend.
  
* A small group of states consistently showed a negative skew (average below median) across all three years: Connecticut, Illinois, Mississippi, Oregon and Wisconsin. A wider group of 10-13 states shows negative skew in any single year, but most of these are inconsistent from year to year, suggesting the wider count includes meaningful estimation noise, while the five consistent states may reflect a genuine, structural feature of those markets.

3. **[How Pay Changed](https://public.tableau.com/views/WageStatistics-HowPayChanged/HowPayChanged?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**
* The change in wage gap between the top 10% vs the bottom 10% from 2023 to 2025 was split evenly between the 50 states. 25 states showed an increasing difference, meaning top 10% earners grew their wages faster than bottom 10%, and the other 25 showed the opposite trend of narrowing inequality. Vermont showed an exceptionally high wage gap, however, this again coincides with Vermonts flagged wage error %.

* Median hourly wages increased for nearly every state, however, North Dakota, Iowa, Massachusetts and California saw a decrease, while staying relatively stagnant in Minnesota, Indiana, Arizona and Arkansas. California's average hourly wage rose over the period even as its median fell, this is a concrete sign of a widening wage gap: a small group of high earners pulled the average up while the typical (median) electrician's pay actually fell. It should be noted that California has by far the largest electrician workforce of any state, exceeding the next-largest by a wide margin.

5. **[Pay vs. Demand](https://public.tableau.com/views/WageStatistics-PayvsDemand/PayvsDemand?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**
* Electrician density (electricians per 1,000 total jobs) increased in 34 states and decreased in 16 between the 2023-2025 period.
* 

## Conclusion


## Limitations


## Tools Used/Dashboard
 * Google Sheets
 * Tableau



