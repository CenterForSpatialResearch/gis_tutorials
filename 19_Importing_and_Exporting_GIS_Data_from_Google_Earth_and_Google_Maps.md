# Importing and Exporting GIS Data from Google Earth and Google Maps

*This tutorial will cover how to visualize GIS data in Google Earth and Google Maps and how to extract data from Google Earth and Google Maps*

## Importing Shapefiles in Google Earth

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

Open Google Earth Pro. Select `Import` from the `File` menu.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

Select your data's file type from `Files of Type` menu. Choose a shapefile from the file type menu and click `Open`.

NOTE: A warning message may appear if your file contains more than 2500 features. You can choose to import a sample of the data, restrict the imported data to your current view, or import all.

Click the `Import All` button.

When prompted to create a Style Template, click `Yes`.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

In the `Style Template Settings` dialog box, you can create a style template including colors, labels, and icons.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

Under the `Color` tab, select `Use single color` and click on the color swatch to choose a color.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

Under the `Height` tab, keep `Clamp features to ground` selected to visualize the data draped over the terrain in Google Earth.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

Click `OK` to finish your style.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

You will be prompted to save the style template for future use.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

The GIS data has now been converted to KML and the data appears in Google Earth. KML files are located under the `Places` panel under the `Temporary Places` folder.


## Creating Features in Google Earth




## Creating Features in Google Maps

You can also create custom maps in [Google Maps](https://www.google.com/mymaps). 

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

Log into your google account and click `CREATE A NEW MAP` in Google My Maps.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

Here you can zoom, pan, and enter and address just as you would use Google Maps online.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

You can add a marker by clicking the `Add marker` button. This will create markers that can be exported as point data.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

You can also draw a line by clicking the `Draw a line` button. This will allow you to draw polylines on layers. Here you have the option to draw a line or shape or compute directions.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

To compute directions, select either `Add driving route`, `Add biking route`, or `Add walking route`. Add a start Destination `A` and an end Destination `B`.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

You can export the data you created in your map by clicking the options to the right of your maps title and selecting `Export to KML`. Here you can specify the layer you wish to export as a KML.

## Importing KML files into ArcGIS

Open ArcGIS. Import any base data you wish to visualize.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

To import the KML files you created in Google Earth and Google Maps, go to `ArcToolbox` > `Conversion` > `KML to Layer`.

![t19-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_19/t19-0.png)

You have now imported the features you created from Google Earth and Google Maps in ArcGIS.