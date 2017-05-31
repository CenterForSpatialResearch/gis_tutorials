# Creating a 3D Site Model in GIS

The purpose of this tutorial is to introduce and explore surface data analysis using a vector data model: TIN (Triangulated Irregular Network). We will load the 3D Analyst Analyst extension, create an elevation model and activate a 3D software browser: ArcScene.

ArcGIS uses an extension called 3D Analyst to visualize and analyze 3D surface data.

This extension allows you to:
  * create digital models of geographic surfaces
  * display the models in three-dimensions using the application ArcScene
  * analyze various properties of these models

![t9-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-0.png)

The first thing you need to do is to create a specific GIS layers that you want to use for your site model. This is best completed using ArcMap. We will make a sub-selection of buildings footprints and roads from a layer downloaded from the [CUGIR](http://cugir.mannlib.cornell.edu/index.jsp) for Orange County New York. We will also use a DEM raster image for Orange County from the same source.

Add all data layers into ArcMap. We will only select buildings and roads that fall on top of the raster image we downloaded.

![t9-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-1.png)

We will also create contours from our raster file that will help build a 3D surface. Using the `Contour` tool, we will create contours at 20ft intervals. Note that since our original elevation file is in meters, we must use a `Z Factor` conversion of 3.2808.

Now you need to switch to ArcScene, the 3D version of ArcMap.

## Importing Contours with Base Heights

Launch ArcScene and add the 20ft Contour Layer we made as a layer.

![t9-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-2.png)

Note that although you are looking at the contours in an isometric view, the contours are lying flat. This is due to the fact that we have not defined their base heights and there is no current Z value in the contour line shapefile / feature class. We will see later that we can permanently assign a Z value to a contour line.

We can now define the contour base heights. Right click on the layer and choose Properties, then click on the Base Heights Tab. Click on the “Use a constant value or expression:

Use the expression builder (Calculator Icon) to select the `Contour` attribute field”

![t9-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-3.png)

Click `OK`, and you'll see the contours are now displayed in 3D.

## Creating a TIN Using Contours

TINs (or Triangulated Irregular Networks) are representations of 3D surfaces that use a set of contiguous, non-overlapping triangles to describe a geographic surface.

TINs can be created from a number of data sources, including points, lines, and polygons. For example:
  *Digitized contour lines (hypsography)
  *Spot elevations from GPS or survey data
  *Satellite LiDAR data or NED data

We can Build a TIN in either ArcMap or ArcScene. We will use ArcScene in this example. Open `ArcToolbox` > `3D Analyst Tools` > `Data Management` > `TIN` > `Create Tin`

![t9-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-4.png)

Make sure you are using the `Height Field` set to the `CONTOUR` field to generate the TIN as we want x,y and z to all be in feet.

Surface feature type (SF_type) The surface feature type helps define the TIN surface and categorizes the input features according to behaviors associated with their vector type. Points, for instance, can only be added as mass points. However, line features can be represented as hard or soft breaklines, and polygons can be `hardclip`, `softclip`, `hardreplace`, `softreplace`, `harderase`, `softerase`, `hardvaluefill`, or `softvaluefill`.

Hard and soft qualifiers for line and polygon feature types are used to indicate whether a distinct break in slope occurs on the surface at their location. A hard line is a distinct break in slope, while a softline will be represented on the surface as a more gradual change in slope.

![t9-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-5.png)

Choose the `Softline` option here as the contour lines are representations of gradual slopes without a sudden break mapped by a given isopleth or contour line.

![t9-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-6.png)

Click `OK` and the TIN is created. After a few minutes (depending on the speed and memory of your computer), the TIN should display in ArcScene, and you have your first digital terrain model.

## Thematic Display of TINs

ArcScene allows you to change the symbology of your TINs to reflect percentage slope, slope aspect, elevation, etc. The process is very similar to changing the symbology of a layer in ArcMap. Right click on the tin layer and choose Properties. Then click on the Symbology tab.

![t9-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-7.png)

With Elevation loaded and checked, uncheck the Edge Types and Faces and click to exit out of the Properties menu and view the result.

![t9-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-8.png)

In the top left corner, you have the option to choose what to display. Click the Add button and you will have the option to select from a number of different display modes. Choose the option you desire and click Add. When finished, click Dismiss.

![t9-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-9.png)

Now, experiment with different themes. Try displaying the TIN with `Slope Percentage`. You might have to rearrange the color ramps to get a good display. Note that depending the resolution of your contour interval, the TIN may take a while to generate.

![t9-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-10.png)

We will use a single color for the next part of the tutorial. We can preview this by using the `Elevation` renderer with only 1 class.

## Draping Layers on Your TIN

ArcScene allows you to drape other layers on top of your TIN or raster images. For example, you can drape the streets layer to give the streets a Z value. Or you can drape an orthophoto of the area.

![t9-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-11.png)

Add 2D road and building layers to ArcScene. You can see them lying flat under the TIN surface with no elevation assigned to them.

![t9-12.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-12.png)

Right click on the road layer and choose `Properties`. Then click on the `Base Height` tab, select your `TIN` as the `Base Height` and float the streets on top of the custom surface or `TIN`. The roads are now displayed in 3D.

![t9-13.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-13.png)

You can also display buildings in 3D by providing a `Base Height` and extruding them a given distance above the base height. Add buildings to your ArcScene. Place them on the TIN surface by defining the `Base Heights`. Right-click on the building layer, go to `Properties` and open the `Base Heights` tab. In there, check the option `Floating on a Custom Surface` and GIS will automatically select the raster file with the topography data. Once you say `OK`, the buildings will adjust to the terrain information provided by the raster file. If you look closely under them, and if your terrain has some variation you will notice that the buildings have different base heights.

![t9-14.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-14.png)

Then, right-click on the layer and go to `Properties`. Here go to the `Extrusion` tab and check `Extrude Features in Layer`. Since our data does not have associated height data, we will extrude the data by 80 feet. You could also click on the calculator icon to the right of the `Extrusion value` or `Expression box` and choose the field that represents the height of the buildings to extrude. Click `OK`, and you will see how your buildings are now extruded.

![t9-15.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-15.png)

You can also change the way ArcScene handles shadows, lighting, and even the background color. Right click on `Scene Layers` and click on `Scene Properties`. Here you can use the `Illumination` tab to deal with shading by changing the Azimuth and Altitude specifications.

## Draping an Ortho Image on Your TIN

Download an ortho-image from an online resource. Add the image to ArcScene. Select `Yes` to build pyramids to refresh the image at a faster rate in ArcScene.

![t9-16.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-16.png)

The image will import flat in ArcScene. Right click on the image layer and select `Properties`. Float the image on the TIN surface we created in the `Base Heights` tab and the image will conform to the geometry of the TIN surface.

## Exporting your 3D data to Rhino or 3DS Max

Note: It is recommended that you only export one layer at a time, particularly when exporting topography or buildings.

![t9-17.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-17.png)

Go to `File` > `Export Scene` > `3D`. Save your file (the only option is `VRML` format). Depending on how big your file is, this might take some time.

Import the `.vrml` file you just saved. You need to change the type of file to `all files` in order to see this file format. Once you import it you will notice that the file is all one mesh and that it has been rotated 90 degrees.

You can rotate it back to its normal position and delete the camera that comes with it.

![t9-18.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_09/t9-18.png)

You have now imported your 3D data you created in ArcScene as a 3D site model in CAD format.
