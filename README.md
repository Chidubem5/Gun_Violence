# Gun Violence Heat Map


## [► Proportional Impact — Who Bears the Burden?](https://chidubem5.github.io/Gun_Violence/gun_violence_disparity.html)
> For each race group and sex: % of national population vs % of gun deaths side by side. The wider the gap, the more disproportionately affected. Bottom panel shows death rate per 100k of each group's own population over time.

## [► Combined View — Heat Map + State Rankings](https://chidubem5.github.io/Gun_Violence/gun_violence_combined.html)
> Heat map and ranked bar chart side by side. Hover over a state on either chart to highlight it on the other. Shared play button and year slider animate both together.

## [► Heat Map Only](https://chidubem5.github.io/Gun_Violence/gun_violence_heatmap.html)
> Hover over any state to see gun death totals, race breakdown, and sex breakdown. Use the slider to move through years 1999–2024.

## [► View the Race Bar Chart](https://chidubem5.github.io/Gun_Violence/gun_violence_race_bar_chart.html)
> States ranked highest → lowest by gun death rate. Select a race group from the dropdown and animate through years 1999–2024.

---

This project explores U.S. gun deaths through an interactive heat map with breakdowns by state, race, and sex over time. The goal is to make patterns visible and comparable across geography and demographics while keeping the focus on population‑adjusted rates.

### How "Gun Death" Is Defined

All deaths are drawn from CDC WONDER Underlying Cause of Death data. A death is counted as a gun death if its ICD‑10 underlying cause code is one of the following 12 codes:

| Code | Description |
|------|-------------|
| W32 | Accidental handgun discharge |
| W33 | Accidental rifle, shotgun, and larger firearm discharge |
| W34 | Accidental discharge from other and unspecified firearms |
| X72 | Intentional self‑harm by handgun discharge |
| X73 | Intentional self‑harm by rifle, shotgun, and larger firearm discharge |
| X74 | Intentional self‑harm by other and unspecified firearm discharge |
| X93 | Assault by handgun discharge |
| X94 | Assault by rifle, shotgun, and larger firearm discharge |
| X95 | Assault by other and unspecified firearm discharge |
| Y22 | Handgun discharge, undetermined intent |
| Y23 | Rifle, shotgun, and larger firearm discharge, undetermined intent |
| Y24 | Other and unspecified firearm discharge, undetermined intent |

Together these cover every manner of death (accident, suicide, homicide, and undetermined intent) in which a firearm was the underlying cause.

### Population Denominators (how the "per 100k" rates are computed)

Every rate on every page is `deaths / population * 100,000`. The **deaths** numerator comes from
the two CDC WONDER exports in this repo. The **population** denominator does **not** come from
those exports' own `Population` column — CDC WONDER suppresses any State x Year x Race x Sex cell
with fewer than 10 deaths, and when a cell is suppressed its population is also dropped from the
export, not zeroed out. Summing that column (as an earlier version of this pipeline did) silently
undercounts the true population and inflates every rate, more so in earlier years when small-count
suppression was more common — which manufactured a spurious upward trend over time.

Population denominators are instead pulled directly from the **U.S. Census Bureau Population
Estimates Program (PEP)**, which publishes population by state, year, sex, and race independent of
any mortality data and is not subject to CDC's death-count suppression:

- **1999**: `ST-99-43` (age x race x sex x Hispanic origin, by state)
- **2000–2009**: `st-est00int-alldata.csv` (intercensal estimates, rebased to the 2000 Census)
- **2010–2020**: `SC-EST2020-ALLDATA6.csv` (Vintage 2020 estimates)
- **2021–2024**: `sc-est2024-alldata6.csv` (Vintage 2024 estimates)

All pulled with `ORIGIN=0` (total, regardless of Hispanic origin) to match how CDC WONDER's race
grouping variable is defined — CDC's race categories are not Hispanic-origin-exclusive.

**Known limitations of this approach**, disclosed rather than silently absorbed:

1. **1999 vintage mismatch.** The 1999 file is the original (pre-2000-Census) postcensal estimate;
   2000 onward uses estimates rebased to the 2000 Census. National population is ~2% lower in the
   1999 source than a 2000-Census-consistent figure would show. This creates a small (~2%),
   known step between 1999 and 2000 that is a vintage artifact, not real population change.
2. **Bridged-race vs. race-alone.** CDC's 1999–2017 bridged-race mortality data is paired here with
   Census "race alone" population tallies (not the bridged-race population product NCHS uses
   internally), since a public bridged-race population file by state/year/sex was not available.
   The two are close but not identical — bridged-race counts fold multiracial respondents into
   single-race buckets by a probabilistic algorithm that "race alone" does not. Expect low
   single-digit-percent differences in race-specific rates for 1999–2017 as a result.
3. **2018–2024 race shares sum to ~97%, not 100%.** CDC's "Single Race 6" mortality categorization
   (White / Black / AIAN / Asian / NHOPI) has no bucket for "Two or more races" (~2–3% of the U.S.
   population). The population denominators used for the 5 tracked groups therefore only cover
   ~97% of each state's residents in this period — this is a category-coverage gap in CDC's own
   scheme, not an error in the population source.
4. **Death totals for any given state/year can still be a slight undercount** where a specific
   race/sex cell was suppressed (fewer than 10 deaths, exact count not published). This is
   unavoidable with public CDC WONDER data; the app labels affected states/groups as suppressed
   in the map, tooltip, and bar chart rather than treating a missing cell as zero.

None of the above resembles the original bug: population shares now sum to ~97–100% per year
(not the 137% previously observed), and no state's "Overall" rate can mathematically exceed its
largest subgroup rate, since Overall is always `total deaths / true total population`, not a
subgroup population divided by the count of race categories present that year.

Main Features:
- Interactive heat map of gun death rates by state
- Time slider to move across years
- Breakdowns by race and sex
- Clear, reproducible data sources (preferably government datasets)

Next Step:
- Explore race‑on‑race crimes by pairing perpetrator and victim data. The key challenge is finding a source that includes both in a consistent format so comparisons are accurate.

Limitations:
- Access to appropriate, consistently defined perpetrator/victim data is limited and often fragmented across sources.

Policy Context (Data Availability):
- In January 2025, White House actions targeted what the administration called “gender ideology” in the federal government and rescinded prior federal equity initiatives. One executive order defined federal sex terminology in binary terms, and another rescinded earlier equity‑related orders.
- Agencies subsequently reviewed or pulled material tied to gender identity, LGBT health, DEI, and related public health topics. Reporting at the time noted that some CDC pages and datasets (e.g., HIV, youth health, and other public health resources) were removed or revised during compliance reviews.
