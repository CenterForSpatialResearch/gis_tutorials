# Exporting 3D Data and Importing in Rhino and 3DS Max

Below are intructions on how to import 3D data from ArcScene into Rhino and 3DS Max

Note: It is recommended that you only export one layer at a time, particularly when exporting topography or buildings.

![t10-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_10/t10-0.png)

Once you have your 3D data imported in ArcScene, go to `File` > `Export Scene` > `3D`. Save your file (the only option is `VRML` format). Depending on how big your file is, this might take some time.

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
