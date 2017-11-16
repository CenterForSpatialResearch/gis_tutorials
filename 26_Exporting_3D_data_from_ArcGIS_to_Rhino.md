# Exporting 3D Data from ArcGIS to Rhino

## Visualizing 3D Data in ArcScene

Make a 3D file in ArcScene using this [tutorial](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/05_Visualizing_Data_in_3D_Using_ArcScene.md).

## Exporting Data

Enable the `Data Interoperability` and `3D Analyst` extensions by going to `Customize --> Extensions` in the toolbar of either ArcCatalog or ArcScene. Failure to do so will result in the necessary tools not running
![t26-0.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-0.png)
![t26-1.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-1.png)

Go to the `layer 3D to Feature Class` tool in `Arctoolbox --> 3D Analyst tools --> Conversion`
This tells arcscene that the layer is a mesh object that can be transformed to other relevant file types. Selecting the `folder` button to the right of the `Output Feature Class` address bar lets you change the destination and name of the output file
![t26-2.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-2.png)
![t26-3.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-3.png)

Select `Quick Export` from `Arctoolbox --> Data Interoperability tools`. Click the `null` export type and change it to Autodesk 3ds. Select the folder in which to save the file.
![t26-4.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-4.png)
![t26-5.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-5.png)
![t26-6.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-6.png)

## Importing to Rhino
`Import` the file into Rhino. You can edit the Rhino import settings if you wish, or you can just leave it default. You might need to `Zoom Extents` to find the location of the objects.
![t26-7.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-7.png)

You`ll notice that the faces of the objects imported from ArcScene render incorrectly so to fix that, you need to `select all` and `explode` the meshes. Now, all faces should be rendered properly on all sides.
![t26-8.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-8.png)
![t26-9.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-9.png)


## Importing with Z axis intact
If the ArcScene layers have X, Y and Z axes, i.e. floating on a contour surface or particular z axis heights, you can still import them to Rhino at those heights. Refer to [this tutorial](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/09_Creating_A_3D_Site_Model_In_GIS.md) for help with this. Select `feature to 3D by attribute` from `Arctoolbox --> 3D Analyst Tools --> Feature to 3D by Attribute`. This essentially allows you to set the heights at which each feature is extruded from using a particular attribute.
![t26-10.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-10.png)

Select the `height field` as the `Z axis`, which would be the base heights of the features (ground elevation in this case). This process can also be used for making contour lines 3D.
![t26-11.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-11.png)

Afterwards, extrude to the heights of each feature by rightclicking on the layer name and going to ` Properties`. Navigate to the tab titled `Extrusions` and check `Extrude features in layer`. To set the `extrusion value`, click the `calculator` to the right of `Extrusion value or expression`.
![t26-12.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-12.png)

After this, repeat the process of exporting `layer 3D to feature class` and `importing` to Rhino.


## Exporting contour lines for Rhino
Select `export to CAD` from `Conversion Tools --> To CAD.` This tools let you export a layer or multiple layers to CAD, at which point you can then`import` to Rhino. The CAD file will already be 3D if its base heights were already set up in ArcScene.
![t26-13.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-13.png)
![t26-14.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-14.png)
![t26-15.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_26/t26-15.png)
