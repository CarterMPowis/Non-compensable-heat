## Overview

This set of scripts was used to generate the number of lethal heat days per year for
years between 1971 - 2100 and warming levels 0.5 - 4 degrees.

To use these scripts you must install the lethal_heat package to your environment.
This can only be done using the github repository.

## CMIP6 Analysis Scripts

These scripts are listed roughly in the order of analysis.

### 1. cmip6_calculate_temp_rh_min_max

This is a preprocessing step.
Calculate daily temperature and humidity min and max, and upload them to google bucket.
This is used to index the lookup table for number of hours per day.

### 2. create_lethal_heat_lookup
Quick script for using Vecellio22.create_lookup_table() to create and save a lethal heat lookup table.


### 3. cmip6_daily_lethal_heat_hours_lookup

Estimates the number of lethal heat hours per day in CMIP6 data using the lookup table method.

Temperature max, min, and RH max and min are assumed to exist on a google bucket.
These are pulled down in the analysis.

### 4. cmip6_ndays_over_lethal_heat

Takes daily lethal heat hour count, and counts the number of lethal heat days per year.
Allows for multiple definitions of a 'lethal heat day' in terms of the 
number of hours per day.

This uses existing hours_over_lh files, which contain the daily number of hours per day over LH. It fetches them from a remote bucket in batches.

Hour count files are output from cmip6_daily_lethal_heat_hours.ipynb

## HADISD Analysis Scripts
