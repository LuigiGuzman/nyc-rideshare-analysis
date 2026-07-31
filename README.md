# NYC Rideshare Demand Analysis: Weather & Holidays

## Overview
Analysis of NYC Uber pickup data (January-June 2015) to examine how weather conditions and holidays affect rideshare demand across the city's boroughs. This is a follow-up to an earlier Boston rideshare project, using a larger, more geographically diverse dataset to test similar hypotheses about weather's effect on demand.

## Business Questions
1. Does temperature affect ride demand?
2. Does precipitation (rain/snow) affect ride demand?
3. Do holidays increase or decrease ride demand?

## Data Source
Kaggle: [NYC Uber Pickups with Weather and Holidays](https://www.kaggle.com/datasets/yannisp/uber-pickups-enriched)
- Original size: 29,101 rows, 13 columns
- Cleaned size: 26,058 rows, 13 columns
- Time period: January 1 - June 30, 2015

## Data Cleaning Process
- Removed 3,043 rows with missing `borough` values. Investigation showed these rows had very low pickup counts (mean ~2, max 11) compared to the dataset average (mean ~490), and were not concentrated on holidays as an initial small sample misleadingly suggested — a full-count check corrected that assumption. These appear to be unmatched/unassigned trips rather than a meaningful category.
- Verified zero duplicate rows
- Verified no impossible values (pickups, temperature, wind speed, and precipitation all fell within realistic ranges)

## Data Integrity Check
Each borough had exactly 4,343 rows — a uniform structure reflecting one row per hour per borough, not an indication of fabricated data. To confirm the underlying pickup values were genuine, I checked average pickups by borough: Manhattan (2,387) far exceeded Brooklyn (534), Queens (309), Bronx (51), Staten Island (1.6), and EWR/Newark Airport (0.02) — matching real-world NYC geography and population density.

## Findings

### 1. Temperature and Demand
Average pickups increase steadily with temperature, from ~510 in cold weather (<32°F) to ~690 in warm weather (70°F+). This pattern holds consistently across every borough when checked individually, not just in the citywide average.

### 2. Precipitation and Demand
Rain/snow days show slightly *lower* average pickups (~520) compared to dry days (~570) — a modest effect, opposite to the intuition that bad weather increases rideshare reliance.

### 3. Holidays and Demand
Non-holidays show higher average pickups (~550) than holidays (~490). This likely reflects NYC's commuter-driven volume: holidays remove a large share of daily office-commute trips, outweighing any potential increase from holiday travel or events. This finding is specific to how "holiday" is defined in this dataset (official holidays) and may not extend to specific high-demand event nights (concerts, games) or to less commuter-dependent cities.

## Conclusion
This project builds on lessons from an earlier Boston rideshare analysis — verifying data integrity before drawing conclusions, and testing hypotheses honestly even when results don't match initial expectations. Temperature showed a clear, consistent relationship with demand across all boroughs. Precipitation and holidays both showed mild effects, in some cases opposite to initial intuition, underscoring the value of testing assumptions against real data rather than assuming a hypothesis will hold.

## Tools Used
Python (Pandas, Matplotlib), Google Colab
