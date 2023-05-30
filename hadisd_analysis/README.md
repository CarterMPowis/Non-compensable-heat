## Overview

This set of scripts was used to generate the number of lethal heat days per year for
years between 1971 - 2100 and warming levels 0.5 - 4 degrees using CMIP6 data.
These are the scripts used to generate the results presented in (Powis et al., 2023).

To use these scripts you must install the lethal_heat package to your environment.
This can only be done using the github repository:

https://github.com/davbyr/lethal_heat

* cmip6_analysis: Notebooks for lethal heat analysis of CMIP6 data.
* hadisd_analysis: Notebooks for lethal heat analysis of HADISD data

In addition, there is a notebook called create_lethal_heat_lookup.ipynb.
This is used to generate the lookup table used in CMIP scripts.

Paper reference:

TBD

## HADISD Analysis Scripts

### hadisd_lethal_heat_6_largest_distances

For HADISD data, calculates 'lethal distances'. I.E. the distance from the lethal curve according to Vecellio 2022.
For this distance data, the 6 largest values through the year are chosen and saved.
