
# NC COVID-19 zip code data

This is a running repository for data captured daily by reporters from WRAL News via the [N.C. Department of Health and Human Services' zip code-level map](https://www.ncdhhs.gov/divisions/public-health/covid19/covid-19-nc-case-count#zip-code-map) of COVID-19 cases and deaths.

## Methodology

For now, this process is being completed manually, but the next steps will be to automate the process.

We're using [py esri dump](https://github.com/openaddresses/pyesridump) to capture the raw data from the [map layer published daily](https://nc.maps.arcgis.com/home/item.html?id=52f127a0767149ec984e91fcc06b06cb#overview) via the State of North Carolina's ArcGIS account. [The rest endpoint is here](https://services.arcgis.com/iFBq2AW9XO0jYYF7/arcgis/rest/services/Covid19byZIPnew/FeatureServer/0). (Note: Although DHHS first published its zip code map April 30, the agency started using this new layer on May 4. The endpoint for this map may change again).

**Usage**

    esri2geojson https://services.arcgis.com/iFBq2AW9XO0jYYF7/arcgis/rest/services/Covid19byZIPnew/FeatureServer/0 nc_zipDATE.geojson
After the geoJSON file is captured, we can upload it to [MapShaper](https://mapshaper.org/) to reduce the file size to 10 percent to speed up load times and download as a simplified geojson file.

We're also using [QGIS software](https://qgis.org/en/site/) to export the file in CSV format.

Once DHHS publishes the new file around 11 a.m., we can process the data and update [our own map](https://www.wral.com/coronavirus/nc-coronavirus-cases-maps-graphs-live-updates/19010016/) accordingly.

**5/20 UPDATE:** DHHS changed its [data dashboard](https://covid19.ncdhhs.gov/dashboard) on May 20 ~~and no longer appears to be updating the data in the shapefile layer. I'm checking with the agency on whether this will change in the future~~. But in the meantime, the process takes a little more time.

[Tableau](https://www.tableau.com/), the platform DHHS is using to visualize its data, is not set up to allow direct downloads in a structured format, but you can download ZIP code data as a PDF. We're then using [Tabula PDF](https://tabula.technology/) to convert this PDF to a spreadsheet and matching that spreadsheet with previous ZIP code data (population count, place name, etc.) to keep the formatting consistent with past versions of the data.

The PDF produced by the Tableau download omits ZIP codes where:

 1. the population is less than 500 AND case count is less than 5
 2. the case count is zero.

All 779 N.C. zip codes, including zero case count values, **are** included in the post-May 20 data below. Case counts are blank where the population is less than 500 and case count less than 5.

**5/23 UPDATE:** Correcting the information above, N.C. DHHS **is** still updating [its shapefile through ArcGIS](https://nc.maps.arcgis.com/home/item.html?id=52f127a0767149ec984e91fcc06b06cb#overview). To stay consistent, I will continue to use that data in our map and provide it here (aside from the several days I missed when I was trying to gather info from the state about its plans for the data going forward, which I will try to track down and backfill).

The state considers the data on its new Tableau dashboard to be the most up-to-date zip code information. But the shapefiles used by that platform are slightly different than those used in the ArcGIS platform (ZIP codes [are not standardized shapes](https://carto.com/blog/zip-codes-spatial-analysis/), per se, and change often). Because both platforms provide some level of data cleaning/geocoding to place addresses in the appropriate zip codes when aggregating cases and deaths, numbers on the state's new dashboard may not align 100% with the ArcGIS data used for WRAL's map.

## Data
Below are the time-series files starting with the first date of capture on May 1. We'll eventually start combining these into a single file to show growth over time.
 - May 1 | [CSV file](time_series_data/csv/nc_zip0501.csv) *(geojson files not captured)*
 - May 2 | [full geoJSON file](time_series_data/full_geojson/nc_zip0502.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0502.json) | [CSV file](time_series_data/csv/nc_zip0502.csv)
 - May 3 | [full geoJSON file](time_series_data/full_geojson/nc_zip0503.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0503.json) | [CSV file](time_series_data/csv/nc_zip0503.csv)
 - May 4 | [full geoJSON file](time_series_data/full_geojson/nc_zip0504.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0504.json) | [CSV file](time_series_data/csv/nc_zip0504.csv)
 - May 5 | [full geoJSON file](time_series_data/full_geojson/nc_zip0505.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0505.json) | [CSV file](time_series_data/csv/nc_zip0505.csv)
 - May 6 | [full geoJSON file](time_series_data/full_geojson/nc_zip0506.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0506.json) | [CSV file](time_series_data/csv/nc_zip0506.csv)
 - May 7 | [full geoJSON file](time_series_data/full_geojson/nc_zip0507.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0507.json) | [CSV file](time_series_data/csv/nc_zip0507.csv)
 - May 8 | [full geoJSON file](time_series_data/full_geojson/nc_zip0508.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0508.json) | [CSV file](time_series_data/csv/nc_zip0508.csv)
 - May 9 | [full geoJSON file](time_series_data/full_geojson/nc_zip0509.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0509.json) | [CSV file](time_series_data/csv/nc_zip0509.csv)
 - May 10 | [full geoJSON file](time_series_data/full_geojson/nc_zip0510.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0510.json) | [CSV file](time_series_data/csv/nc_zip0510.csv)
 - May 11 | [full geoJSON file](time_series_data/full_geojson/nc_zip0511.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0511.json) | [CSV file](time_series_data/csv/nc_zip0511.csv)
 - May 12 | [full geoJSON file](time_series_data/full_geojson/nc_zip0512.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0512.json) | [CSV file](time_series_data/csv/nc_zip0512.csv)
 - May 13 | [full geoJSON file](time_series_data/full_geojson/nc_zip0513.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0513.json) | [CSV file](time_series_data/csv/nc_zip0513.csv)
 - May 14 | [full geoJSON file](time_series_data/full_geojson/nc_zip0514.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0514.json) | [CSV file](time_series_data/csv/nc_zip0514.csv)
 - May 15 | [full geoJSON file](time_series_data/full_geojson/nc_zip0515.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0515.json) | [CSV file](time_series_data/csv/nc_zip0515.csv)
 - May 16 | [full geoJSON file](time_series_data/full_geojson/nc_zip0516.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0516.json) | [CSV file](time_series_data/csv/nc_zip0516.csv)
 - May 17 | [full geoJSON file](time_series_data/full_geojson/nc_zip0517.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0517.json) | [CSV file](time_series_data/csv/nc_zip0517.csv)
 - May 18 | [full geoJSON file](time_series_data/full_geojson/nc_zip0518.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0518.json) | [CSV file](time_series_data/csv/nc_zip0518.csv)
 - May 19 | [full geoJSON file](time_series_data/full_geojson/nc_zip0519.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0519.json) | [CSV file](time_series_data/csv/nc_zip0519.csv)
 - May 20 | [CSV file](time_series_data/csv/nc_zip0520.csv) *(see note above)*
 - May 21 | *(data pending)*
 - May 22 | *(data pending)*
 - May 23 | [full geoJSON file](time_series_data/full_geojson/nc_zip0523.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0523.json) | [CSV file](time_series_data/csv/nc_zip0523.csv)
 - May 24 | [full geoJSON file](time_series_data/full_geojson/nc_zip0524.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0524.json) | [CSV file](time_series_data/csv/nc_zip0524.csv)
 - May 25 | [full geoJSON file](time_series_data/full_geojson/nc_zip0525.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0525.json) | [CSV file](time_series_data/csv/nc_zip0525.csv)
 - May 26 | [full geoJSON file](time_series_data/full_geojson/nc_zip0526.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0526.json) | [CSV file](time_series_data/csv/nc_zip0526.csv)
 - May 27 | [full geoJSON file](time_series_data/full_geojson/nc_zip0527.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0527.json) | [CSV file](time_series_data/csv/nc_zip0527.csv)
 - May 28 | [full geoJSON file](time_series_data/full_geojson/nc_zip0528.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0528.json) | [CSV file](time_series_data/csv/nc_zip0528.csv)
 - May 29 | [full geoJSON file](time_series_data/full_geojson/nc_zip0529.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0529.json) | [CSV file](time_series_data/csv/nc_zip0529.csv)
 - May 30 | [full geoJSON file](time_series_data/full_geojson/nc_zip0530.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0530.json) | [CSV file](time_series_data/csv/nc_zip0530.csv)
 - May 31 | [full geoJSON file](time_series_data/full_geojson/nc_zip0531.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0531.json) | [CSV file](time_series_data/csv/nc_zip0531.csv)
 - June 1 | [full geoJSON file](time_series_data/full_geojson/nc_zip0601.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0601.json) | [CSV file](time_series_data/csv/nc_zip0601.csv)
 - June 2 | [full geoJSON file](time_series_data/full_geojson/nc_zip0602.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0602.json) | [CSV file](time_series_data/csv/nc_zip0602.csv)
 - June 3 | [full geoJSON file](time_series_data/full_geojson/nc_zip0603.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0603.json) | [CSV file](time_series_data/csv/nc_zip0603.csv)
 - June 4 | [full geoJSON file](time_series_data/full_geojson/nc_zip0604.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0604.json) | [CSV file](time_series_data/csv/nc_zip0604.csv)
 - June 5 | [full geoJSON file](time_series_data/full_geojson/nc_zip0605.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0605.json) | [CSV file](time_series_data/csv/nc_zip0605.csv)
 - June 6 | [full geoJSON file](time_series_data/full_geojson/nc_zip0606.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0606.json) | [CSV file](time_series_data/csv/nc_zip0606.csv)
 - June 7 | [full geoJSON file](time_series_data/full_geojson/nc_zip0607.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0607.json) | [CSV file](time_series_data/csv/nc_zip0607.csv)
 - June 8 | [full geoJSON file](time_series_data/full_geojson/nc_zip0608.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0608.json) | [CSV file](time_series_data/csv/nc_zip0608.csv)
 - June 9 | [full geoJSON file](time_series_data/full_geojson/nc_zip0609.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0609.json) | [CSV file](time_series_data/csv/nc_zip0609.csv)
 - June 10 | [full geoJSON file](time_series_data/full_geojson/nc_zip0610.geojson) | [reduced geoJSON file](time_series_data/reduced_geojson/nc_zip0610.json) | [CSV file](time_series_data/csv/nc_zip0610.csv)