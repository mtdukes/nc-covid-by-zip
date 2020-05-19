
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

## Data
Below are the time-series files starting with the first date of capture on May 1. We'll eventually start combining these into a single file to show growth over time.
 - May 1 | [CSV file](time_series_data/csv/nc_zip0501.csv) (geojson files not captured)
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