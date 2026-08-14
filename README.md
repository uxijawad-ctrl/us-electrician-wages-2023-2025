## **State-Level Wage Trends for Electricians in the US from 2023 to 2025**

### **Abstract**
The US is facing a well-documented shortage of skilled tradespeople. The BLS projects 9% growth in electrician employment from 2024 to 2034, alongside roughly 81,000 annual openings and the National Electrical Contractors Association (NECA) report that close to 30% of union electricians are nearing retirement age. Yet it remains unclear whether wages are rising fast enough to attract new workers into the trade at the pace demand requires. This project uses BLS OEWS data from 2023 to 2025 to examine whether electrician wages across states show signs of stagnation or growing inequality, one possible lens on why the labor gap persists despite rising demand.

### **Data Source**
Bureau of Labor Statistics - Occupational Employment Wage Statistics (OEWS)

### **Methodology**
All figures below are drawn from BLS OEWS state-level estimates. Each estimate carries a published margin of error for both employment and wage figures. States with error bands flagged "High" in either metric (thresholds calibrated to this dataset: employment error >8%, wage error >4%) are noted individually and treated with caution rather than excluded outright. Where a finding depends on a flagged state, a sensitivity check (recalculating with that state removed) was run to confirm the result holds.

### **Methodology Note**
A small number of state-year estimates carry notably higher margins of error than the rest of the dataset, most consistently Vermont (2025 wage error: 7.4%, up from 0.8% in 2024) and Maine (2025 employment error: 9.1%), both small-workforce states where BLS sampling produces less stable percentile estimates. These states are flagged throughout, and any headline ranking they appear in is noted accordingly.

### **Tools Used**
* Google Sheets
* Tableau

### **Main Questions**
* Which 10 states paid electricians the highest avg. hourly wage in 2023, 2024 and 2025 and which 10 states paid the lowest avg. hourly wage?
* How does the average vs median wage compare per state?
* Which states have the widest spread between bottom 10% and top 10% wage earners?
* Which states saw the largest % increase in avg. hourly wage over the three years?
* Are top earners (90th percentile) growing faster than bottom earners (10th percentile) in certain states?
* Which states have the highest electrician density (electricians per 1,000 jobs)? Does higher density correlate with lower or higher wages (supply/demand effect)?
* Which states have the largest total employment growth between 2023-2025, and does that align with wage growth or dilute it?

### **Key Findings**
* A small number of states show high margins of errors in wage and employment data, most notably Vermont (2025 wage error was 7.4%, up from 0.8% in 2024) and Maine (2025 employment error was 9.1%). Both are states with a small workforce where BLS sampling produces unstable percentile estimates. These states are flagged and noted throughout.
  
* Average hourly wage increased for nearly every state between 2023 to 2025 - some exceptions were North Dakota, Iowa, Massachusetts, New Mexico, New York, Mississippi and California where wages either declined or stayed relatively stagnant.
  
* Median hourly wages saw a similar trend, where they increased in most states but North Dakota, Iowa, Massachusetts and California saw a decrease, while staying relatively stagnant in Minnesota, Indiana, Arizona and Arkansas.
  
* Looking across all states, the maximum wage gap recorded has trended downward from 2023-2025, however there were variations on a state level where some states narrowed their wage gap while others widened it.

  <img width="568" height="321" alt="Where Pay Stands" src="https://github.com/user-attachments/assets/96bb3a7c-46a6-43f7-8ec9-90fd75cbf5c8" />

  
* A small group of states consistently showed a negative skew (average below median) across all three years: Connecticut, Illinois, Mississippi, Oregon and Wisconsin. A wider group of 10-13 states shows negative skew in any single year, but most of these are inconsistent from year to year, suggesting the wider count includes meaningful estimation noise, while the five consistent states may reflect a genuine, structural feature of those markets.
  
* The difference between the top 10% vs the bottom 10% wage growth was split evenly between the 50 states. 25 states showed an increasing difference, meaning top 10% earners grew their wages faster than bottom 10%, and the other 25% showed the opposite trend between 2023-2025.
  
* Electrician density (electricians per 1,000 total jobs) increased in 34 states and decreased in 16 over the period.

  <img width="575" height="333" alt="How Pay Changed" src="https://github.com/user-attachments/assets/5e60d133-29d7-45a5-9131-5124c8acaef4" />


* A scatter plot of % change in electrician density against % change in wages showed a weak negative correlation. States where the electrician workforce grew faster relative to the overall job market showed a slight tendency toward slower wage growth, however this relationship is weak.

* California has by far the largest electrician workforce of any state, exceeding the next-largest by a wide margin. A separate scatter plot of % change in total employment against % change in wages shows a similarly weak negative correlation.

* A further test examined whether states with faster-growing electrician employment also showed a widening or narrowing average-median gap over time. This correlation was negligible, indicating that workforce growth does not meaningfully predict whether a state's wage distribution becomes more or less concentrated at the top.

  <img width="581" height="338" alt="Pay vs Demand" src="https://github.com/user-attachments/assets/afafaf54-b8aa-4a67-a360-edbea23d9fc9" />













