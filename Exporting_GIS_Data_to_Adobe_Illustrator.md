# Exporting GIS Data to Adobe Illustrator

*This tutorial will guide you through the process of exporting GIS shapefiles for use as vector files in Adobe Illustrator.*

Most of the time after finishing your map in GIS you will still want to do some formatting in Illustrator because it is much better for styling, setting lineweights, and fills. However, sometimes the layers will not be imported correctly into Illustrator, they will be rasterized and grouped into a single layer. In addition, some elements are exported as text characters which might not be recognized. Here are some general exporting tips and some solutions to these problems.

* Make sure that you’ve included all the necessary elements and layers in your map before exporting it. Once you have your map in Illustrator it is very difficult to bring in more layers and make them match. Also remember to include a scale bar, a north arrow and possibly a legend (all under the insert menu in the layout view).

* Make sure that you don’t have any transparencies before you export. If you want to use transparencies, you can always apply them in Illustrator. You can also change the fill color, outline color, and outline weight of any layer in Illustrator.

* Make sure your layers are not nested in any group layers.

* If you include any special characters such as a north arrow make sure you convert them to graphics before you export. Just right-click on the special character and click the “convert to graphics” option. You can also ungroup the scale bar or the north arrow here if that is something you want to do.

* Make sure that the scale bar is in the right units. GIS will default to feet, which, for most maps is not adequate. You can do this by right-clicking on the scale bar and going to Properties/Units.

Export your map in `File` > `Export Map…` Here, change the type to `.ai` (Adobe Illustrator). Under the Options menu adjust the DPI; 150-200 dpi should be fine if you are not planning on zooming in on your map. In the Format Option change the Picture Symbol to Vectorize Bitmap or Picture Symbol Fills. And check the Convert Marker Symbols to Polygons box.

![t3-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_03/t3_1.PNG)

You should be able to open up your file in Illustrator and access all of your layers. Illustrator will invariably say that some of the characters were not recognized and that you need to update them. Click yes. After this, you should be able to see your map.

However, if some of your layers have been converted to strips of rasters, you should go back to ArcMap and recheck all of the things mentioned above. A good strategy to find out which layers are causing problems is to only export some of them and see if they come up fine in Illustrator. This way you will be able to isolate the layers that are causing the problem.

Finally, if one of your layers has too many vertices, Illustrator will rasterize it no matter what. Unfortunately, there is no way around this.

![t3-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_03/t3_2.png)

Once in Illustrator you will notice that your layers will have been grouped and that a clipping mask will have been created for each piece of geometry. You can always release the clipping masks manually, but generally there are too many objects in the map to make this feasible. The quickest solution is to select an object in a layer using the `Direct Selection Tool` (the white arrow - this will select the geometry and not the clipping mask). From the `Select` drop-down menu, go to `Same` > `Appearance` (for this to work correctly, each layer must have been exported with different colors from ArcGIS).

![t3-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_03/t3_3.PNG)

This will select all geometry that has a similar appearance to the selected geometry which (assuming your exported ArcGIS file is formatted correctly) should be all elements in the data layer. Then navigate to the `Layers` panel and create a new empty layer. You should see a colored square (it should be the same color as the selected object's layer) next to one of the original layers in the exported file. Click and drag this colored square to your newly created empty layer to copy the geometry without the clipping masks.

Repeat this step for all of the exported data layers. It is good practice to name the new layers based on their content (e.g. "building footprints", "street centerlines", etc.). You can now delete the original layers (with the layer masks), and still be able to change the appearance of geometry by layer instead of having to color each item individually.
