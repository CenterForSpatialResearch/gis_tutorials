# Exporting 3D Data and Importing in Rhino and 3DS Max

Below are instructions on how to import 3D data from ArcScene into Rhino and 3DS Max. This tutorial uses the following datasets:
* [Building footprints](https://data.cityofnewyork.us/Housing-Development/Building-Footprints/nqwf-w8eh)
* [NYC 3D Building Model](http://www1.nyc.gov/site/doitt/initiatives/3d-building.page), the "Multipatch (ESRI)" file, which has much better resolution and includes building setbacks.

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

Other files called Multipatch files can be imported that already contain detailed 3D information. This data includes details such as roof setbacks and roof slopes. For New York City, a multipatch database can be found under the Department of City Planning website.

It is recommended that you make a selection of the area you wish to model before exporting, so you will not export large amounts of unnecessary data.

![t10-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-0.png)

Once you have your 3D data imported in ArcScene, go to `File` > `Export Scene` > `3D`. Save your file (the only option is `VRML` format). Depending on how big your file is, this might take some time.

Note: It is recommended that you only export one layer at a time, particularly when exporting topography or buildings.

![t10-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-1.png)

## Importing 3D Data in Rhino

Once you have done this open Rhino. Make sure your units are in feet. The default units are in Millimeters when opening Rhino but this is not useful with most GIS data.

![t10-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-2.png)

Import the `.vrml` file you just saved. You need to change the type of file to `all files` in order to see this file format. Once you import it you will notice that the file is all one mesh and that it has been rotated 90 degrees.

![t10-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-3.png)

![t10-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-4.png)

You can rotate it back to its normal position and delete the camera that comes with it.

![t10-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-5.png)

Although the buildings are triangulated with vertices, they will render perfectly.

![t10-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-6.png)

If you want to modify the buildings in any way you can always explode the mesh and convert it to NURBS using the `MeshToNURBS` command. However, you have to be careful with this because if you have too many buildings you might crash your computer.

Another method is to export a building footprint layer from GIS to CAD, and then in Rhino, change the base heights and extrude the buildings using the mesh as a “snapping” reference. However, you will have to do this for every single building. The advantage is that you will have a site model that is built only with polysurfaces.

## Importing 3D Data in 3DS Max

Importing the .vrml file is much simpler in 3DS Max as meshes are the native geometry.

![t10-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-8.png)

Go to the command button at the top left and navigate to `import` > `import`.

![t10-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-9.png)

A dialog box will appear. You have the options to `Reset Scene`, `Turn to 3DS Coordinates`, and to create `Primitives`. We will continue as default since we are working in a new file. If you were to import additional data you would uncheck `Reset Scene.`

![t10-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-10.png)

Your 3D data will now be displayed in 3DS Max.
