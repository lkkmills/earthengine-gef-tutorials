# earthengine-gef-tutorials

This repository is a collection of tutorials and guides for GEF data collection on Google Earth Engine (GEE). Tutorials are sorted by project ID, and they walk through the collection process for each relevant boundary. Some tutorials require imported data, and those datasets can be found in the "data" folder.

## Table of Contents:
* [Working with geoBoundaries data](#working-with-geoboundaries-data)
   * How to download data from geoBoundaries
   * How to visualize data from geoBoundaries
* [Uploading data to Google Earth Engine](#uploading-data-to-google-earth-engine)

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
