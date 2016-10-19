# Downloading Vector Data in Grasshopper using Meerkat

This tutorial uses Meerkat Beta version 1.6c available via [Food4Rhino](http://www.food4rhino.com/project/meerkatgis?ufh)

Several plug-ins available for Grasshopper enable the use of spatial data in Grasshopper via online sources. This tutorial will cover how to download vector data in Grasshopper using the Meerkat plug-in.

## Loading GIS Data using Meerkat

*IMPORTANT: This tutorial requires an internet connection*

![t14-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-0.png)

Install the Meerkat plug in by copying all appropriate files into the Grasshopper Components folder, accessed in Grasshopper under `File` > `Special Folders` > `Component Folder`. You will have to unblock all `.dll` files and `.gha` files by right clicking on the file > `Properties` > `Unblock` at the bottom of the `General` tab. Now restart Grasshopper and a new tab for Meerkat components should be displayed in the `Extra` tab.

![t14-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-1.png)

Load the `Import Shapefile` component and `Parse Meerkat File` from the Meerkat menu.

![t14-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-2.png)

Right click on the `On-Off` input of the `Input Shapefile` component and set the boolean to `True` in `Set Boolean`.

A Meerkat dialog box will appear with a Google Satellite Image loaded on the screen. Just like in Google Maps online, you can pan and zoom around the map and toggle between `Map` and `Satellite` view.

![t14-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-3.png)

You can add shapefiles to your map from your computer by clicking `Add Shape File`. We will add a shapefile for the buildings of the Columbia University campus builings. Make sure the checkbox next to your loaded shapefile is activated in the left menu panel. The map will automatically zoom to the region of your shapefile.

![t14-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-4.png)

We will add another shapefile for the pavement for New York City. Add the data using the `Add Shape File` button and navigate to your shapefile. If you toggle the checkbox in the left menu bar the window will zoom to the extent of both your shapefiles.

![t14-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-5.png)

Using the `Draw a rectangle` tool to the right of the `pan` tool, select a region of interest in your map by drawing a rectangle on the map. We will zoom back into the Columbia University region to make our selection.

![t14-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-6.png)

Just like the `Clip` tool in ArcGIS, we can clip our data in Meerkat using the `Crop Shape File(s)` button. You will need to specify a directory for the map to create its output file. Once you specify the output, the data will begin to crop to your window. The file will be saved as a `.mkgis` file. However, unlike the `Clip` tool in ArcGIS, the data is not physically trimmed but selected to the region of your interest. You can use a `Trim with Regions` component in Grasshopper if you wish to physically trim the data once imported.

## Parsing .mkgis Files in Grasshopper

![t14-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-7.png)

In the Grasshopper window, load a `File Path` component and connect it to the `Meerkat File` input of the `Parse.mkgis` component. Set the data in the `File Path` to the building parcels file.

![t14-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-8.png)

The outputs of the `Parse.mkgis` display various information about the file. The output also includes one option for `Field Names` and one option for `Field Values per Shape`. Connect a panel to each of these outputs to see the attributes from the original shapefile that can be used to visualize the data in Grasshopper.

## Visualizing GIS data in Grasshopper using Meerkat

![t14-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-9.png)

To visualize the data you created in the Rhino viewport, create an `Area` component and attach it to the `Bounds in Point Space` output of the `Parse.mkgis` component. Add a `Construct Point` component with the `X`, `Y`, and `Z` inputs set to `0` and a `Vector 2Pt` component. Attach the `Pt` output of the `Construct Point` component to the `B` input of the `Vector 2Pt` component and attach the `C` centroid output of the `Area` component to the `A` input of the `Vector 2Pt` component.

Create a `Move` component and attach the `Geometry per Shape` output of the Parse.mkgis` component to the input `G`. Attach the `V` vector output of the `Vector 2Pt` component to the `T` Motion input of the `Move` component. 

Your data will now be displayed as points in the Rhino viewport.

![t14-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-10.png)

Add a `Polyline` component and attach the `G` geometry output of the `Move` component to the `V` vertices input. This will draw the outline of each building footprint.

![t14-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_14/t14-11.png)

We can continue to add data to our file. We will load the roads using the same process.

The advantage to using Meerkat to load shapefiles is the ability to quickly crop shapefiles to a selected region and the ability to read the attributes of the shapefiles.