# Importing and Exporting GIS Data from Google Earth and Google Maps

*This tutorial will cover how to visualize GIS data in Google Earth and Google Maps and how to extract data from Google Earth and Google Maps*

In this tutorial we will cover how to load shapefiles into Google Earth, how to draw features in both Google Earth and Google Maps, and how to export your features as a KML file for importing into ArcGIS.

This tutorial utilizes Google Earth Pro, Google Maps online, and ArcGIS 10.4.1.

## Importing Shapefiles in Google Earth

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

Open Google Earth Pro. Select `Import` from the `File` menu.

![t19-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-1.png)

Change the list of viewable files to `All Files (*.*)`. Choose a shapefile (AutoCAD Shape Source File) from the file type menu and click `Open`.

NOTE: A warning message may appear if your file contains more than 2500 features. You can choose to import a sample of the data, restrict the imported data to your current view, or import all.

Click the `Import All` button.

When prompted to create a Style Template, click `Yes`.

![t19-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-2.png)

In the `Style Template Settings` dialog box, you can create a style template including colors, labels, and icons.

![t19-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-3.png)

Under the `Color` tab, select `Use single color` and click on the color swatch to choose a color.

![t19-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-4.png)

Under the `Height` tab, keep `Clamp features to ground` selected to visualize the data draped over the terrain in Google Earth.

Click `OK` to finish your style.

![t19-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-5.png)

You will be prompted to save the style template for future use.

![t19-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-6.png)

The GIS data has now been converted to KML and the data appears in Google Earth. KML files are located under the `Places` panel under the `Temporary Places` folder.

## Creating Features in Google Earth

You can create features in Google Earth using the `Add Placemark`, `Add Polygon`, `Add Path` and `Add Image Overlay` tools in the toolbar at the top of Google Earth.

![t19-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-7.png)

To add placemarks, click the `Add Placemark` button. Drag your placemark to the location you want on the map or specify coordinates of latitude and longitude. You wil be asked to name your file and change color stles if you wish.

![t19-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-8.png)

Continue to add Placemarks. You can group your placemark in a layer by going to `Add` in the menu bar and navigating to `Layer`. Then drag your Placemarks into the Layer.

![t19-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-9.png)

You can also add lines and polygons by tracing features on the map. Click on the `Add Polygons` button. You will be asked to name your polygon. Before closing the dialog box, begin tracing your features.

![t19-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-10.png)

Once you have finished creating your features, save them as KML files by right clicking on the feature or Layer in the `Places` window and selecting `Save Place As...`. You can change the file type to KML in the dropdown menu at the bottom of the dialog box.

## Creating Features in Google Maps

You can also create custom maps in [Google Maps](https://www.google.com/mymaps). 

![t19-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-11.png)

Log into your google account and click `CREATE A NEW MAP` in Google My Maps.

![t19-12.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-12.png)

Here you can zoom, pan, and enter and address just as you would use Google Maps online.

![t19-13.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-13.png)

You can add a marker by clicking the `Add marker` button. This will create markers that can be exported as point data.

![t19-14.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-14.png)

You can also draw a line by clicking the `Draw a line` button. This will allow you to draw polylines on layers. Here you have the option to draw a line or shape or compute directions.

![t19-15.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-15.png)

To compute directions, select either `Add driving route`, `Add biking route`, or `Add walking route`. Add a start Destination `A` and an end Destination `B`.

![t19-16.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-16.png)

You can export the data you created in your map by clicking the options to the right of your maps title and selecting `Export to KML`. Here you can specify the layer you wish to export as a KML.

## Importing KML files into ArcGIS

![t19-17.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-17.png)

Open ArcGIS. Import any base data you wish to visualize.

![t19-18.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-18.png)

To import the KML files you created in Google Earth and Google Maps, go to `ArcToolbox` > `Conversion Tools` > `From KML` > `KML to Layer`.

![t19-19.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-19.png)

Right click on the imported data layers to export them as a shapefile with the same coordinate system as your map.

You have now imported the features you created from Google Earth and Google Maps in ArcGIS. You can also export features from ArcGIS as KML files for use in Google Earth Pro and Google Maps using the `Layer to KML` tool to save your shapefiles as a KML file. Once exported you will be able to open these files in Google Earth Pro and Google Maps.