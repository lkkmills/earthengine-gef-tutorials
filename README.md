# earthengine-gef-tutorials

This repository is a collection of tutorials and guides for GEF data collection on Google Earth Engine (GEE). Tutorials are sorted by project ID, and they walk through the collection process for each relevant boundary. Some tutorials require imported data, and those datasets can be found in the "data" folder.

## Table of Contents:
* [How to use this repository](#how-to-use-this-repository)
* [Working with geoBoundaries data](#working-with-geoboundaries-data)
   * [How to download data from geoBoundaries](#how-to-download-data-from-geoboundaries)
   * [How to visualize data from geoBoundaries](#how-to-visualize-data-from-geoboundaries)
* [Uploading data into Google Earth Engine](#uploading-data-into-google-earth-engine)
* [Using data within the GEE catalog](#using-data-within-the-gee-catalog)

## How to use this repository

1. Copy and paste the tutorials into your GEE code editor.
2. Import data where specified (either download yourself or refer to the ["data" folder](https://github.com/lkkmills/earthengine-gef-tutorials/tree/main/data)).
3. Use these scripts as building blocks to write your own scripts.

## Working with geoBoundaries data

### How to download data from geoBoundaries

1. Navigate to the [geoBoundaries website](https://www.geoboundaries.org/).
2. Click ["Download Data"](https://www.geoboundaries.org/index.html#getdata).
3. Filter by the [ISO-3 code](https://unstats.un.org/unsd/tradekb/knowledgebase/country-code) of the country (Vietnam = VNM, Cambodia = KHM, Laos = LAO).
4. Download the administrative level you are looking for (none of our data collection will use ADM0 or ADM1).

![image](https://user-images.githubusercontent.com/76752916/138480197-b771e763-80c8-4626-b464-2706aa8168d6.png)

### How to visualize data from geoBoundaries

1. Navigate to the [geoBoundaries website](https://www.geoboundaries.org/).
2. Click ["Visualize Data"](https://www.geoboundaries.org/geoContrast.html?country=NIC&mainSource=geoBoundaries+%28Open%29&comparisonSource=GADM+v3.6&mainLevel=1&comparisonLevel=1).
3. Choose a country (ex. Laos).
4. Compare the boundaries for different ADM levels (I usually compare ADM1 and ADM2).

![image](https://user-images.githubusercontent.com/76752916/138480626-823852b5-5a36-4ea0-8b18-dd0ed6b0e36d.png)

5. Scroll down the page to "Matching". Here, you can see the names of all the ADM1 boundaries versus all the names of ADM2 boundaries.

![image](https://user-images.githubusercontent.com/76752916/138482084-ad486cd4-626f-4300-8256-c33e349863fc.png)

#### Why is this tool helpful?
For our data collection, we will only be using ADM2 and higher. If you read a document report and want to know which administrative level a boundary belongs to, this tool helps you visualize and check.

## Uploading data to Google Earth Engine

Read: [Importing Table Data](https://developers.google.com/earth-engine/guides/table_upload)

## Using data within the GEE catalog

As an example, we'll import the [World Database on Protected Areas (WDPA)](https://developers.google.com/earth-engine/datasets/catalog/WCMC_WDPA_current_polygons) from the data catalog.

"The World Database on Protected Areas (WDPA) is the most up-to-date and complete source of information on protected areas, updated monthly with submissions from governments, non-governmental organizations, landowners, and communities. It is managed by the United Nations Environment Programme's World Conservation Monitoring Centre (UNEP-WCMC) with support from IUCN and its World Commission on Protected Areas (WCPA)."

Features & FeatureCollections
* [Feature Overview](https://developers.google.com/earth-engine/guides/features)
* [FeatureCollection Overview](https://developers.google.com/earth-engine/guides/feature_collections)
* [Feature and FeatureCollection Visualization](https://developers.google.com/earth-engine/guides/feature_collections_visualizing)
* [FeatureCollection Information and Metadata](https://developers.google.com/earth-engine/guides/feature_collection_info)
* [Filtering a FeatureCollection](https://developers.google.com/earth-engine/guides/feature_collection_filtering)
* [Mapping Over a FeatureCollection](https://developers.google.com/earth-engine/guides/feature_collection_mapping)
* [Reducing a FeatureCollection](https://developers.google.com/earth-engine/guides/feature_collection_reducing)

Earth Engine hosts a variety of table datasets. To load a table dataset, provide the table ID to the FeatureCollection constructor. 

For example, to load WDPA data, copy the Earth Engine snippet from here:

https://developers.google.com/earth-engine/datasets/catalog/WCMC_WDPA_current_polygons

The Earth Engine snippet is the following:

ee.FeatureCollection("WCMC/WDPA/current/polygons")

Code block that can be copied directly into GEE:

```
var dataset = ee.FeatureCollection('WCMC/WDPA/current/polygons');

var visParams = {
  palette: ['2ed033', '5aff05', '67b9ff', '5844ff', '0a7618', '2c05ff'],
  min: 0.0,
  max: 1550000.0,
  opacity: 0.8,
}; // Visualization parameters

var image = ee.Image().float().paint(dataset, 'REP_AREA');

Map.setCenter(41.104, -17.724, 6);
Map.addLayer(image, visParams, 'WCMC/WDPA/current/polygons');
Map.addLayer(dataset, null, 'for Inspector', false);
```
