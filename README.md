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

## CMIP6 Analysis Scripts

These scripts are listed roughly in the order of analysis.

### 1. cmip6_calculate_temp_rh_min_max
This is a preprocessing step.
Calculate daily temperature and humidity min and max, and upload them to google bucket.
This is used to index the lookup table for number of hours per day.
Assumes  the temperature and humidity data already exists on a google bucket. The data
is pulled down in batches for analysis using `gsutil`.

### 2. cmip6_daily_lethal_heat_hours_lookup

Estimates the number of lethal heat hours per day in CMIP6 data using the lookup table method.

Temperature max, min, and RH max and min are assumed to exist on a google bucket.
These are pulled down in the analysis.

### 3. cmip6_ndays_over_lethal_heat

Takes daily lethal heat hour count, and counts the number of lethal heat days per year.
Allows for multiple definitions of a 'lethal heat day' in terms of the 
number of hours per day.

This uses existing hours_over_lh files, which contain the daily number of hours per day over LH. It fetches them from a remote bucket in batches.

Hour count files are output from cmip6_daily_lethal_heat_hours.ipynb

### 4. cmip6_convert_timeperiod_to_warminglevels
Converts the analysis in the third script to an analysis by warming level, rather than by year.

## HADISD Analysis Scripts

### hadisd_lethal_heat_6_largest_distances

For HADISD data, calculates 'lethal distances'. I.E. the distance from the lethal curve according to Vecellio 2022.
For this distance data, the 6 largest values through the year are chosen and saved.

## GEV Analysis Scripts

### hadisd_gev_analysis 

Cleans HADISD data, conducts a Kolmogorov-Smirnov test to ensure station block maxima can be described by a GEV distribution, performs a likelihood ratio test to ensure station block maxima are better described by a non-stationary GEV distribution where the location parameter is a linear function of global average temperature, and finally uses fitted non-stationary GEV distributions to calculate return periods for non-compensable heat events under different global warming outcomes. 


