# Downloading and Converting Raster Data from the Web

Below are intructions on how to download topographic data for International data from the Earth Explorer, for the USA from USGS, and for New York State using the Cornell University Geospatial Information Repository (CUGIR).

## Downloading International Data using the USGS Earth Explorer

The United States Geological Survey (USGS) makes a wide array of data available to the public through their EarthExplorer server.Among this data is topographic information. The following tutorial will walk you through downloading this topographic data from the website.

![t6-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-0.png)

In your web browser, navigate to [earthexplorer.usgs.gov](earthexplorer.usgs.gov).

You will have to resister and make an account to download files on this website.

The main interface of the seamless server is relatively simple to use and is similar to other web map platforms. Use the `Zoom` tools to zoom into your area of interest. These tools are located on the bottom right of the map screen. You can also zoom into an area on the map by either using the scroll wheel of your mouse or double clicking on an area of interest. Clicking and dragging on the map window pans the map around. To display different layers of information to help you navigate, use the search options to the left of the map.

![t6-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-1.png)

In the `Search Criteria` tab on the left, enter a place of interest into the `Address/place` tab and click `Show` to locate on the map. You can zoom into your selected region, indicated by a red marker tag.

![t6-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-2.png)

Click on the `Data Sets` tab on the left to search for datasets.

![t6-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-3.png)

Expand the `Digital Elevation` option and select `ASTER GLOBAL DEM`. A dialog box will appear with warnings about using the data. If you approve the usage compliance, click `OK` and continue. Click on `Results a the bottom right hand corner of the `Data Sets` menu.

![t6-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-4.png)

You will be redirected to the `Results` tab showing relevant datasets from your search. You can click on the options in the search entry to expore the metadata or preview a footprint of the data before you download it. When you are satisfied with your selection click the `Download Options` button (the symbol of a green arrow pointing down to a server). 

![t6-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-5.png)

You can now add your downloaded file to your map.

## Downloading data for the USA using the USGS National Map Viewer

The United States Geological Survey (USGS) makes a wide array of data available to the public through their NationalMap server. Among this data is topographic information. The following tutorial will walk you through downloading this topographic data from the website.

![t6-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-6.png)

In your web browser, navigate to [http://nationalmap.gov/viewer.html](http://nationalmap.gov/viewer.html).

![t6-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-7.png)

The main interface of the seamless server is similar to the EarthExplorer server in the previous exercise. Zoom into or query a geography of your interest.

![t6-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-8.png)

Once you have zoomed in to the area for which you are looking for information, make a selection from the `Datasets` tab and click "Find Products" button at the top right of the `Dataset` menu. We will search for `Elevation Products (3DEP)`.

![t6-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-9.png)

A list of available datasets will appear, including the resolution (smaller numbers are higher resolution and cover a smaller area and vice-versa - 1/9 arc second is the highest resolution and is good for zooming in on a specific site and 1 arc second is the lowest resolution and is good for a regional scale), `Data Extent`, and the format (the default choice is `ArcGrid`). 

![t6-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-10.png)

Clicking on `Footprint` or `Thumbnail` will preview your raster image on the map before you download the file. Press `Download` to download the file.

![t6-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-11.png)

You can now add your downloaded file to your map.

## Downloading data for New York State using the CUGIR

The Cornell University Geospatial Information Repository (CUGIR) has a wealth of information on New York State including topographic information. This tutorial will walk you through finding and downloading this information.

In your web browser, navigate to the CUGIR website: [cugir.mannlib.cornel.edu](cugir.mannlib.cornel.edu)

![t6-12.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-12.png)

Click `Browse` in the top menu bar.

![t6-13.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-13.png)

Search for the `Elevation` from the Topics panel. Click `Select` to search for the elevation datasets.

![t6-14.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-14.png)

Select the `Elevation (10m raster)` from the `Data Theme Menu`. The provider for this data is the NYS Department of Environmental Conservation.

![t6-15.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-15.png)

The next page offers a list of all the raster maps available for New York State organized by Mapsheet. You can navigate to your mapsheet of interest and click `download now` in the `Download` column. This will redirect you to a new page to download a zipped download package.

If you do not know which map you need, you can select it by using a map rather than the list of names. To do this, click on the `Map Browse` option in the top menu bar. On the interactive map, click to zoom into your area of interest. Then, select the area for which you need to download information. For your future reference, the name of the map will appear when you hover your mouse cursor over the map. After you select your area, three files will be listed for you to download. The first is the `7.5 Minute Topographic Maps`. These files are georeferenced tiffs. The second is the elevation dataset in the form of a DEM (Digital Elevation Model). The last file is a polyline shapefile of water features for your area. 

![t6-16.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-16.png)

On the next page, download the files you need.

The next section of this tutorial will walk you through using the DEMs you downloaded in ArcMap.

## Using DEM Imagery in ArcMap

Download the DEM information from the previous example. This file will be saved as a `.zip` file. Unzip the whole `.zip` file, then unpackage the `.gz` file within the file. You should now have a `.dem` file ready to use.

![t6-17.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-17.png)

Open ArcMap.

![t6-18.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-18.png)

In `ArcToolbox`, navigate to the `Convert DEM to Raster tool`, which is found in the `Conversion` toolset. Double-click on the tool to open the `DEM to Raster` dialogue box.

![t6-19.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-19.png)

In the dialogue box, navigate to your `.dem` file under `Input USGS DEM file`.
Enter the output location into the `Output Raster` field.
Click `OK`.

![t6-20.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_06/t6-20.png)

Your DEM file should now be converted to a raster that you can use in `ArcGIS`. It will automatically be added to your map project like the image below.