## Visualizing Data in 3D Using ArcScene

*Below are intructions on how to import and visualize data in 3D using ArcScene*

ArcScene is the 3D equivalent to ArcMap. You can use ArcScene to visualize vector and raster data in three dimensions, including changing base heights and extruding volumes.

# Visualizing Vector Data

This exercise uses a building footprint shapefile and visualizes the height of the building by extruding based on height data in the shapefile. This extrusion process can be used with any shapefile and based on any quantitative field in the shapefile's attribute table. For a building height extrusion in New York City, use the latest building footprint data from the NYC Planning website under the MapPLUTO files. The field representing height is called 'HEIGHT_ROO'. This will be used to extrude the building footprints to their appropriate heights. Similarly, the building heights can be extruded using the number of floors as an approximation for height by multiplying the number of floors by an average height of 12-14 feet per floor.

![t5-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-0.png)

Open `ArcScene`. (You will find it at `Programs` > `ArcGIS` > `ArcScene`.) Notice that the interface is very similar to that of `ArcMap`.

![t5-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-1.png)

Add Data. You do this exactly the same way as you would in ArcMap, using the `Add Data` button in the main toolbar.

![t5-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-2.png)

Once you've added your data, it will appear in the window. It will probably appear floating askew, without any volumes. This is because you have not yet assigned an attribute with which `ArcScene` will create volumes.

![t5-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-3.png)

Adding 3D attributes to your map works much like changing or adding symbology to a 2D project in `ArcMap`. Right click on your data layer name in the table of contents and select `Properties`. (Note that one of the tabs in the resulting dialogue box is named `Symbology`. The functions in this tab operate the same as those in `ArcMap`.)

Go to the `Extrusions` tab, and check that you would like to `Extrude features in layer`. Then click the calculator button (on the right) to select or calculate your extrusion heights.

![t5-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-4.png)
 
The `Expression Builder` dialogue box will appear. Note that the `Fields` box on the left contains the data fields associated with this layer. You can extrude your layer based on any of these fields by double-clicking its name in the `Fields` box. You can also manipulate its extrusion through any of the mathematic functions in the `Functions` box or using the calculator buttons on the right. (In the example below, the data layer will be extruded by values in the `HEIGHT_ROO` field.) When you are finished building your expression, click `OK`.

![t5-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-5.png)

We will apply the extrusion by adding it to the feature's minumum height. In the drop down menu `Apply Extrusion by:` choose the option `adding it to each feature's minimum height`.

![t5-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-6.png)

Your layer should now look something like the image below. Each of your layer's polygons will be extruded to volumes. (If you started with a line file, they will be extruded to planes. If you started with a point file, they will be extruded to lines.)

![t5-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-7.png)

Other files called Multipatch files can be imported that already contain detailed 3D information. This data includes details such as roof setbacks and roof slopes. For New York City, a multipatch database can be found under the Department of City Planning website here.

#Visualizing Raster Data

![t5-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-8.png)

Open ArcScene. (You will find it at `Programs` > `ArcGIS` > `ArcScene`.) Notice that the interface is very similar to that of ArcMap.

![t5-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-9.png)

Add Data. You do this exactly the same way as you would in ArcMap or as you would add vector data to `ArcScene`, using the `Add Data` button in the main toolbar.

![t5-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-10.png)

Once you've added your raster data, it will appear in the window. It will appear floating askew, rather than the usual top-down orthographic view you see in `ArcMap`.

Raster data assigns a value to each pixel of the raster image. We usually visualize this data by assigning a color to the values. In the example above, the raster image contains elevation data, with highest elevations represented as white and lowest elevations represented as black.

To visualize raster data in 3D, we change the `Base Height` of each pixel.

![t5-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-11.png)

Right-Click on the layer name in the `Table of Contents`. Select `Properties`. In the `Layer Properties` dialogue box that appears, go to the `Base Heights` tab. There, select `Obtain heights for layer from surface`. This indicates that the values already associated with the raster's pixels are the values you'd like to use for their heights.

If you would like to exaggerate or minimize the new base heights, you can do so by applying a `Z Unit Conversion`. The value you type will be multiplied by the value of each pixel. By default, it is 1. 

Click `OK`.

![t5-12.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_05/t5-12.png)

The result should be a deformation of your original raster image, with a topography corresponding to the values of the data layer's pixels.