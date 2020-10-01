# WRAL COVID-19 dashboard changelog

[WRAL's dashboard of COVID-19 statistics and charts](https://www.wral.com/coronavirus/north-carolina-coronavirus-cases-maps-graphs-live-updates/19010016/) has evolved since its initial launch in the early stage of the pandemic. We'll track changes to our metrics and tracking methodology, and note any corrections to our data here starting on Sept. 5.

## Oct. 1, 2020 - Retiring the unempoyment table

On Oct. 1, 2020, WRAL News noted that the "New unemployment claims in NC" table in its dashboard will no longer be updated. The data, which requires manual collection from the state Division of Employment Security, was updated through July 6.

## Sept. 29, 2020 - Removing congregate settings table

On Sept. 29, WRAL News removed the "COVID-19 outbreaks in NC long-term facilities" table from the dashboard. The N.C. Department of Health and Human Services [continues to publish this data twice weekly in PDF format](https://covid19.ncdhhs.gov/dashboard/outbreaks-and-clusters), but it has become too time-consuming to convert the data into the appropriate format for display on the dashboard.

## Sept. 28, 2020 - Adding antigen cases/deaths/tests

On Sept. 25, the N.C. Department of Health and Human Services announced it was releasing data on both molecular (PCR) and antigen testing in North Carolina. Consistent with [requirements from the Centers for Disease Control and Prevention](https://wwwn.cdc.gov/nndss/conditions/coronavirus-disease-2019-covid-19/case-definition/2020/08/05/), DHHS as of Sept. 25 lists those results separately. Prior to that date, only PCR tests had been included in the total number of tests, cases, deaths etc. Per a DHHS press release:

> Regardless of the test used, a person who tests positive is considered
> to have [COVID-19](https://ncdhhs.us4.list-manage.com/track/click?u=58ec19aaea4630b1baad0e5e4&id=b9e90d74a4&e=9eced87337).
> 
> Molecular (PCR) and antigen tests are used to diagnose COVID-19,
> meaning that they look to see if someone is currently infected with
> COVID-19. Each test looks for something different to determine if
> someone is infected. A molecular (PCR) test looks for the virus’s
> genetic material. An antigen test is a rapid test that looks for
> specific proteins on the surface of the virus. Where the test is
> processed may also differ. Molecular (PCR) tests are processed in a
> laboratory. Antigen tests are often processed at the point of care,
> such as in a health care provider’s office.

DHHS spokesperson Kelly Haight Connor confirmed that the antigen testing data goes back to May 20, and [the agency reports](https://files.nc.gov/covid/documents/dashboard/Antigen-Testing-Frequently-Asked-Questions.pdf) that cases identified through antigen testing make up 2% of the total cases and 0.7% of total deaths due to COVID-19 as of Sept. 25.

Using time-series data of reported cases, deaths and testing  [published by DHHS](https://covid19.ncdhhs.gov/dashboard/about-data), WRAL corrected its own numbers on Sept. 28, for the period from May 20 to Sept. 24.

This correction impacted the following metrics and trend lines on WRAL’s data dashboard:

 - New reported COVID-19 cases, deaths in NC
	 - New cases
	 - New deaths
- COVID-19 testing trends in NC
	- % positive
	- New tests
	- Cumulative tests
- Total reported COVID-19 cases, deaths in NC
	-  Cases
	-  Deaths
- Total COVID-19 cases, deaths by zip code
- Total COVID-19 cases, deaths by county (map)

In addition, the data collected by Johns Hopkins University has also been impacted, resulting in changes to the "New COVID-19 cases by county" time series graph on WRAL's dashboard powered by that data. The Johns Hopkins data did not backfill the new cases from antigen testing, so the addition of antigen test-identified cases appears as a small spike in some counties starting on Sept. 25.

In total, the addition of antigen data added 4,449 cases and 23 deaths to WRAL's dashboard through Sept. 24. For a detailed breakdown of the changes, download a comparison of data for the following metrics captured by WRAL and corrected data published by DHHS as of Sept. 27:

- [Reported and total cases (from May 20 to Sept. 24)](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200927_cases.csv)
- [Reported and total deaths (from Sept. 20, to Sept. 24)](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200927_deaths.csv)
	- DHHS added COVID-19-related deaths identified via antigen tests to the totals starting on Sept. 23. 
- [Testing trends (from Aug. 1 to Sept. 24)](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200927_testing.csv) 
	- WRAL previously tracked testing based on the cumulative number of tests reported each day by DHHS. Data published by DHHS does NOT track testing this way, instead tracking tests by the date they were performed. The number of tests for each day in the DHHS data can change over time as new tests are reported to the agency. Because there is no other way to account for the addition of antigen testing using daily reported cumulative testing, WRAL used DHHS figures from March 17 to Sept. 28 to recalculate all cumulative testing numbers. This had the effect of shifting both the new reported tests and the positivity rate by a day along the timeline.
- [Positivity rates (from May 20 to Sept. 24)](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200927_positivity.csv)
	- WRAL calculates its own positivity rates based on the previous seven days of new reported cases and new tests. With the corrections to both the number of cases and tests, this has been revised both up and down as a function of both the antigen cases/tests and the altered methodology for tracking cumulative tests (see item above).

### Data field layout for [corrections_20200927_cases.csv](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200927_cases.csv)

**date** Date of reported cases, in MM/DD/YYYY format

**dhhs_reported_cases** Corrected number of new reported COVID-19 cases, captured from "Cases by Report Date" published in DHHS' About the Data portal under the Daily Cases and Deaths Metrics tab.

**new_cumulative_cases** Corrected number of new cumulative COVID-19 cases, including those identified by antigen tests, calculated by adding the cumulative number of `dhhs_reported_cases` as of the given date.

**wral_reported_cases** Number of reported new COVID-19 cases tracked by WRAL prior to the addition of antigen testing data. Calculated as the day-over-day difference in cumulative new cases reported by DHHS and captured by WRAL daily.

**old_cumulative_cases** Number of cumulative COVID-19 cases reported by WRAL prior to the addition of antigen testing data. Captured by WRAL daily from the cumulative total cases reported by DHHS.

**new_reported_difference** Change in reported cases with the corrected antigen data, calculated as the difference between `dhhs_reported_cases` and `wral_reported_cases`. 

**cumulative_difference** Change in the number of cumulative cases with corrected antigen data, calculated as the difference between `new_cumulative_cases` and `old_cumulative_cases`.

### Data field layout for [corrections_20200927_deaths.csv](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200927_deaths.csv)

**date** Date of reported deaths, in MM/DD/YYYY format

**dhhs_reported_deaths** Corrected number of new reported COVID-19 deaths, including those identified by antigen tests, calculated as the day-over-day difference between `new_cumulative_deaths` as of the given date.

**new_cumulative_deaths** Corrected number of total COVID-19 deaths, captured from "NC Deaths" published in DHHS' About the Data portal under the Daily Cases and Deaths Metrics tab.

**wral_reported_deaths** Number of reported new COVID-19 deaths tracked by WRAL prior to the addition of antigen testing data. Calculated as the day-over-day difference in cumulative new deaths reported by DHHS and captured by WRAL daily.

**old_cumulative_deaths** Number of cumulative COVID-19 deaths reported by WRAL prior to the addition of antigen testing data. Captured by WRAL daily from the cumulative total deaths reported by DHHS.

**new_reported_difference** Change in reported deaths with the corrected antigen data, calculated as the difference between `dhhs_reported_deaths` and `wral_reported_deaths`. 

**cumulative_difference** Change in the number of cumulative deaths with corrected antigen data, calculated as the difference between `new_cumulative_deaths` and `old_cumulative_deaths`.

### Data field layout for [corrections_20200927_testing.csv](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200927_testing.csv)

**date** Date of reported tests, in MM/DD/YYYY format

**dhhs_reported_tests** Corrected number of new reported COVID-19 tests, captured from "NC Daily Tests" through Sept. 21 published in DHHS' About the Data portal under the Daily Testing Metrics tab. From Sept. 22 on, this figure is calculated as the sum of the "Molecular (PCR) Tests" and the "Antigen Tests" fields from the same data.

**new_cumulative_tests** Corrected number of new cumulative COVID-19 tests, including those identified by antigen tests, calculated by adding the cumulative number of `dhhs_reported_tests` as of the given date.

**wral_reported_tests**  Number of reported new COVID-19 tests tracked by WRAL prior to the addition of antigen testing data. Calculated as the day-over-day difference in cumulative new tests reported by DHHS and captured by WRAL daily.

**old_cumulative_tests** Number of cumulative COVID-19 tests reported by WRAL prior to the addition of antigen testing data. Captured by WRAL daily from the cumulative total tests reported by DHHS.

**new_reported_difference** Change in reported tests with the corrected antigen data, calculated as the difference between `dhhs_reported_tests` and `wral_reported_tests`. 

**cumulative_difference** Change in the number of cumulative tests with corrected antigen data, calculated as the difference between `new_cumulative_tests` and `old_cumulative_tests`.

### Data field layout for [corrections_20200927_positivity.csv](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200927_positivity.csv)

**date** Date of seven-day rolling positivity rate, in MM/DD/YYYY format

**dhhs_reported_cases** Corrected number of new reported COVID-19 cases, captured from "Cases by Report Date" published in DHHS' About the Data portal under the Daily Cases and Deaths Metrics tab.

**wral_reported_cases** Number of reported new COVID-19 cases tracked by WRAL prior to the addition of antigen testing data. Calculated as the day-over-day difference in cumulative new cases reported by DHHS and captured by WRAL daily.

**dhhs_reported_tests** Corrected number of new reported COVID-19 tests, captured from "NC Daily Tests" through Sept. 21 published in DHHS' About the Data portal under the Daily Testing Metrics tab. From Sept. 22 on, this figure is calculated as the sum of the "Molecular (PCR) Tests" and the "Antigen Tests" fields from the same data.

**wral_reported_tests**  Number of reported new COVID-19 tests tracked by WRAL prior to the addition of antigen testing data. Calculated as the day-over-day difference in cumulative new tests reported by DHHS and captured by WRAL daily.

**uncorrected_positivity** Seven-day rolling positivity rate previously reported by WRAL prior to the addition of antigen testing data. Calculated as the sum of the previous seven days' of `wral_reported_cases` divided by the sum of the previous seven days' of `wral_reported_tests` and shown as a percentage.

**corrected_positivity** Seven-day rolling positivity rate recalculated by WRAL with the addition of antigen testing data. Calculated as the sum of the previous seven days' of `dhhs_reported_cases` divided by the sum of the previous seven days' of `dhhs_reported_tests` and shown as a percentage.

**difference** Change in the positivity rate after the antigen data corrections, calculated as the difference between `uncorrected_positivity` and `corrected positivity`. Shown as percentage points.

## Sept. 11, 2020 - Revised methodology

On Sept. 11, WRAL rolled out changes to the county-level chart showing cumulative COVID-19 cases and deaths due to COVID-19.

### Removed metrics

Previous versions of this map included data on **percentage of the population with cases** and the **number of cases in long-term care homes**, both of which were removed in the updated version.

The percentage of the population with confirmed cases has remained too small to provide much value, so we removed it to simplify the graphic and focus on the remaining metrics, like the rate per 100,000 of each county's population. 

Although the state does track ***active*** outbreaks and clusters in long-term care homes by county, it doesn't detail the specific number of cumulative cases by county in its public dashboard. And even county-level data on cases in these congregate facilities can lag, making it hard to compare with numbers updated for each county daily. We removed this metric because it's frequently inaccurate and only occassionally updated.

### Added metrics

The tooltip overlay now includes a calculation for deaths per 100,000 population.

### Changing how we track cases and deaths

WRAL also changed its methodology for tracking and capturing cumulative cases and deaths on the county level. In the initial months of the pandemic, the WRAL reporting team captured real-time data by monitoring individual case counts on both the state level and for each of North Carolina's 100 counties. But as the cumulative totals grew, the variation between state officials' daily updates in the morning or early afternoon and the tally gathered from each county throughout the day became less and less significant. The manual process of comparing and updating each counties changes also delayed daily updates on the map.

WRAL introduced a semi-automated process of downloading county-level data [from the N.C. DHHS dashboard](https://covid19.ncdhhs.gov/dashboard/about-data) from the agency's daily publication of new COVID-19 figures, and we use that data to power the revised county-level map.

We're also independently calculating per population statistics (based on per 100,000 of each county's population) using the July 1, 2019, population estimates from the [U.S. Census Population and Housing Unit Estimates](https://www.census.gov/programs-surveys/popest.html). This might mean slightly different numbers than the state uses for its own calculation (since they're using different population estimates).

## Sept. 10, 2020 - Redesign, revised methodology

On the evening of Sept. 10, WRAL rolled out changes to the chart showing cumulative COVID-19 cases, cumulative COVID-19 deaths and a rolling average of hospitalizations due to COVID-19.

### Redesign of hospitalizations

Because the hospitalization data is a rolling average and not a cumulative total, we separated these figures into their own distinct graph for clarity.

### Redesign of cases/deaths

The large number of cases relative to deaths made the latter hard to see on a combined, so we also separated these metrics into seperate charts, allowing users to swap between them and view each on a variable scale.

### Changing how we track cases and deaths

WRAL also changed its methodology for tracking and capturing these cumulative cases and deaths. In the initial months of the pandemic, the WRAL reporting team captured real-time data by monitoring individual case counts on both the state level and for each of North Carolina's 100 counties. But as the cumulative totals grew, the variation between state officials' daily updates in the morning or early afternoon and the tally gathered from each county throughout the day became less and less significant. We've now reverted to using total case counts published each day by the N.C. Department of Health and Human Services, dating back to when the agency began releasing statewide figures on March 13.

For a detailed breakdown of these changes, download a [comparison of data](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200910.csv) captured by WRAL from the state/county level tracking compared to WRAL's data captured from the N.C. DHHS figures published since March 13 (Note that because the real-time numbers were being updated throughout the day, they're almost always higher than the figures published earlier each morning by NC DHHS that are now used for the graphs).

### Data field layout for [corrections_20200910.csv](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200910.csv)

**date** Date of data capture for either cumulative or real-time cases/deaths

**cumulative_cases_realtime** The sum of new reported COVID-19 cases initially gathered by WRAL and updated continuously throughout the day from state and county health departments.

**cumulative_cases_daily** The cumulative total of lab-confirmed COVID-19 cases published by N.C. DHHS through its statewide dashboard.

**cumulative_cases_difference** The difference between the cumulative number of COVID-19 cases from DHHS (reported around noon each day) and the cumulative total of COVID-19 cases tracked by WRAL throughout the given date.

**cumulative_deaths_realtime** The sum of new reported COVID-19 deaths initially gathered by WRAL and updated continuously throughout the day from state and county health departments.

**cumulative_deaths_daily** The cumulative total of COVID-19 deaths published by N.C. DHHS through its statewide dashboard.

**cumulative_differences_deaths** The difference between the cumulative number of COVID-19 deaths from DHHS (reported around noon each day) and the cumulative total of COVID-19 deaths tracked by WRAL throughout the given date.

## Sept. 5, 2020 - Correction

During the week of Aug. 30, the N.C. Department of Health and Human Services made corrections to its reported case counts for several days in August after LabCorp reported a delay of nearly 1,000 positive test results.

DHHS posted the following explanation on its data dashboard ~~Sept. 3~~ Aug. 31 *(correcting date disclosure was first posted)*:

> On August 29, 2020, LabCorp submitted approximately 1,163 positive
> tests results for which the majority were completed during the first
> of half of August 2020. Because one person may have multiple tests,
> these tests represent 886 unique cases. This submission caused an
> artificially high number of cases reported for August 29. These 886
> cases have now been distributed to the dates in August when they would
> have been reported to the state.

And in response to follow-up questions on Sept. 4, DHHS spokesperson SarahLewis Peel wrote via email: 

> In updating the NC COVID-19 county-level cases data impacted by the
> LabCorp data delays, cases were distributed to the dates in August
> when they would have been reported to the state. However, the delayed
> data on 8/29 that had been received were not subtracted from that
> day’s date.
> 
> On 9/4 at 4:35 p.m. NCDHHS updated all state and county-level cases
> data on the NC COVID-19 dashboards impacted by the LabCorp data
> delays.

Using time-series data of reported cases [published by DHHS](https://public.tableau.com/views/NCDHHS_COVID-19_DataDownload/DailyMetrics?:showVizHome=no), WRAL corrected its own numbers at about 3 p.m., Sept. 5, for the period from Aug. 1 to Sept. 5. The changes ultimately redistributed 886 positive cases across 23 days in August 2020.

This correction impacted the following metrics and trend lines on WRAL's data dashboard:

 - Reported new cases
 - 7-day rolling average of reported new cases
 - 7-day rolling average of tests reported positive

For a detailed breakdown of the changes, [download a comparison of data](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200905.csv) captured by WRAL from Aug. 1 to Sept. 5 and corrected data published by DHHS as of Sept. 5.

### Data field layout for [corrections_20200905.csv](https://github.com/mtdukes/nc-covid-by-zip/blob/master/misc_corrected_data/data/corrections_20200905.csv)

**date** Date of reported cases, in MM/DD/YYYY format

**reported_cases_uncorrected** Number of reported cases based on WRAL's data, calculated by subtracting the current date's total number of cases from the total number of cases from the previous date.

**running_total_uncorrected** Total number of positive COVID-19 cases by date, captured by WRAL daily via the [DHHS Cases dashboard](https://covid19.ncdhhs.gov/dashboard/cases).

**reported_cases_corrected** Number of corrected daily reported cases published by date by DHHS on its [About the Data](https://public.tableau.com/views/NCDHHS_COVID-19_DataDownload/DailyMetrics?:showVizHome=no) portal, downloaded in spreadsheet format by WRAL on Sept. 5.

**running_total_corrected** Total number of corrected positive COVID-19 cases by date, generated by calculating the running total of daily reported cases from DHHS.

**reported_cases_difference** The difference calculated between reported daily cases corrected by DHHS and uncorrected reported daily cases collected by WRAL.

**running_total_difference** The difference calculated between total cases corrected by DHHS and uncorrected total cases collected by WRAL.