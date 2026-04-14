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
