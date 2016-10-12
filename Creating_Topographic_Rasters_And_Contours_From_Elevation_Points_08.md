# Creating Topographic Contours from Elevation Points and Rasters

Below are intructions on how to create topographic rasters and contours from spot elevation points in ArcGIS.

This tutorial will cover the creation and use of elevation data in two parts. The first half will show how to turn point data into a raster file, and the second will show how to generate polyline contours from raster information.

In this tutorial, we will be taking surveyed spot elevation data provided by New York City’s OpenData portal and generating a topographic elevation raster and topography contours.

![t8-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-0.png)

Up to date elevation data is directly available through New York City’s OpenData portal here: [Elevation Points](https://data.cityofnewyork.us/Transportation/Elevation-points/szwg-xci6)

## Creating a Topographic Raster

Unzip the file you downloaded from the NYC OpenData portal. Create a new map in ArcMap and add the new data layer.

![t8-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-1.png)

This dataset contains over a million points and includes multiple types of elevation measurement. Before we can generate our elevation raster, we first need to reduce the  data to a workable size and limit our selection to only spot elevations.

## Sorting the Data

![t8-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-2.png)

Using the selection tools (Select by rectangle, polygon, lasso, circle, line, etc.) select the area of interest for your project. One the selection has been made, right click on the data layer and navigate to `Data` > `Export Data`. Save the selection as a new shapefile. Click `Yes` to add the new shapefile to the map.

![t8-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-3.png)

Reducing the number of points you are working with will drastically speed up the later steps (and reduce the likelihood that they will fail or crash your computer). If you are looking to map the entire city or a larger regional area, you can get pre-made elevation rasters from either Cornell’s CUGIR service (for New York State) or the USGS (for anywhere else in the United States). Refer to the tutorials for Using CUGIR State Topographic Data and Using USGS National Topographic Data.

From this selection, we want to isolate the spot elevations from the other points. To find out what to search for, we will need to check this dataset's metadata and attributes.

![t8-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-4.png)

If we look at the metadata on the NYC OpenData portal website we see that there are four subtypes 

Under the subtypes, the types of elevations provided and the identification system it uses include : Water Elevations (3010), and Building Elevations (3020), Spot Elevations (300000), and Bridge Elevations (300020).

![t8-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-5.png)

Now go to the attribute table by right clicking on the data layer and clicking `Open Attribute Table`. Notice the field named subcode has entries with values matching the metadata found online.

![t8-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-6.png)

Limit the selection of points to only Spot Elevations with the `Select by Attribute` command under `Selection` > `Select by Attribute` on the main pull-down menu bar. Now follow the steps to enter the appropriate formula.

	* Ensure the selection will be made on the appropriate shapefile. 
	* Set the `Method` field to `Create a new selection`. This will make sure we only isolate Spot Elevations from our currently selected subset. * This function makes selections by searching through the attributes table of the shapefile, based on a search query that we will provide. In this case, we only want points with the `sub_code` value of `300000` (which we learned from the metadata). 
	* In the list of fields, double click `sub_code` to add it to our query followed by an equals sign (=). 
	* Then click the `Get Unique Values` to load all possible values, and double click `300000` to complete the query, which should read: `“sub_code” = 300000`.
	* Hit `OK` to complete the new selection.

![t8-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-7.png)

Now our selection of only Spot Elevation Points has been made.

![t8-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-8.png)

Export the selected points as a new dataset by right-clicking on the layer and going to `Data` > `Export Data`.

## Interpolating Point Data

![t8-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-9.png)

Open the `Extensions` panel, under `Customize` > `Extensions...` on the main pull-down menu. Ensure that `3D Analyst` and `Spatial Analyst` are both checked and hit `Close`.

![t8-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-10.png)

Open the `ArcToolbox` Panel and navigate to `Spatial Analyst Tools` > `Interpolation` > `Topo to Raster`. Double-click to open the command.

![t8-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-11.png)

* Select the elevation points file you selected earlier in the `Input Feature Data` pull-down and it should then show up in the panel below. Change the `Field` to `elevation`. Change the `Type` to `PointElevation`. Choose a destination for the output raster file under `Output Surface Raster`. Your new file name must be less than 11 characters. The value of `Output Cell Size` determines the resolution of the raster file and is set by default (reduce the value for a higher resolution output, but this will come at the expense of speed). Set `Primary Type of Input Data` to `SPOT`. The other options can be left as-is.

Hit `OK` and allow the program to generate the raster file.

![t8-12.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-12.png)

The output raster file should be added automatically to the layers of the current map. 

![t8-13.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-13.png)

To change how the raster layer is displayed, right-click the layer, open the Properties menu, and go to the `Symbology` tab. Change the symbology from a `Classified` display to a `Stretched` display and it will display as a grayscale raster image.

## Generating Topographic Contours

This section will show you how to create contours from a raster file. Typically, we use this method to generate topography lines, but you can also use this process for non-elevation raster data.

![t8-14.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-14.png)

Open the ArcToolbox panel and navigate to `3D Analyst Tools` > `Raster Surface` > `Contour`. Double-click to open the command.

![t8-15.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-15.png)

In the contour panel, select the elevation raster file in the `Input Raster` field. Set the destination for the output contour polylines in the `Output Polyline Features` field. It’s good practice to include the contour interval in the file name for easy reference (e.g. `nyc_contours_2ft.shp`). Set the contour interval in `Contour Interval` field. Smaller intervals will take longer to compute.

These intervals will be in the units of the original elevation file which, in the case of this tutorial, is in US Feet. If you are working with a file in meters and need to generate contours in feet, use the `Z Factor` field to enter the conversion factor. When going from meters to feet, the set the value to `0.3048`. For feet to meters conversion, set the factor to `3.2808`. Otherwise, leave the `Z Factor` value at it’s default of `1.0`.

![t8-16.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-16.png)

Hit `OK` to generate the contours. Once the program has completed computing the contours, they should automatically be added to the current map.

The output contour polylines are 2D Geometry, with their elevation value contained in the `CONTOUR` field of their Attribute Table. These can be converted to 3D Geometry (setting each contour to a corresponding height in the Z-axis) using the `Feature to 3D by Attribute` command.

![t8-17.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-17.png)

In the `ArcToolbox` Panel, navigate to `3D Analyst Tools` > `3D Features` > `Feature to 3D By Attribute` and double-click to open.

![t8-18.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-18.png)

In the panel, select the 2D contour lines under the `Input Features` field, and select a destination for the 3D contours under the `Output Feature Class` field. It is good practice to include “3d” in the file name for reference). Set the `Height Field` to the `CONTOUR` attribute, and hit `OK`.

![t8-19.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_08/t8-19.png)

The output contours should automatically be added to the current map. They will appear identical to the 2D contours in ArcMap, but if you export them to CAD and open in Rhino or AutoCAD, they will be placed correctly on the Z-axis.