# Taking Sections through 2D Raster Maps

Below are intructions on how to use extract sectional profiles from 2D Raster Maps in ArcGIS.

## Taking Sections Through 2D Raster Maps

Many 2D Raster mappings (such as elevation models) contain information you may want to communicate with a section cut. The Profile Tool in ArcGIS's 3D Analyst allows you to do this.

![t7-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_07/t7-0.png)

Open `ArcMap` and add your raster map.

![t7-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_07/t7-1.png)

First, make sure that your 3D Analyst extension is enabled. To do this click `Customize` > `Extensions...` from the main pull-down menus. 

![t7-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_07/t7-2.png)

In the dialog box, make sure that `3D Analyst` is checked, and click `Close`.

![t7-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_07/t7-3.png)

Next, add the `3D Analyst` toolbar to your interface if it is not already present. To do this Right-Click on any toolbar or go to the Customize > Toolbars from the main pull-down menus. A list of toolbars will appear. Click "3D Analyst," and the 3D Analyst toolbar will appear.

## Using the `Profile` Tool:

Using the `Interpolate Line Tool`, draw the line of your section on the raster map.

![t7-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_07/t7-4.png)

This line can have as many vertices as needed. For instance, you can find a section along a street or river that is not simply straight. When you are finished with your line, double-click. If you are unsatified, you can delete your line by hitting `delete` when it is highlighted with a bounding box. When you are finished drawing your line, click the `Profile Graph` button on the `3D Analyst` toolbar.

![t7-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_07/t7-5.png)

An image of your profile graph. The units on the x-axis reflect the units of your map (feet, miles, meters, etc) along the line you drew. The values on the y-axis reflect the values (and units) represented by the pixels of your raster map.

![t7-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_07/t7-6.png)

* To export this graph, you can right click on the graph window's title bar and choose to export. You will have your option of formats to export to, including vector graphics. These can then be scaled in a 3D or Vector editing program to the correct proportions.