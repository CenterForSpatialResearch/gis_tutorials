# Importing Topography in Grasshopper Using DTM

*This tutorial will cover how to download, import, and visualize topography in Grasshopper using the DTM (Digital Terrain Mesh) Plug-in*

This tutorial uses DTM (Digital Terrain Mesh) version 0.5 available via [Food4Rhino](http://www.food4rhino.com/app/dtm-digital-terrain-mesh)

This tutorial uses Rhinoceros 5.0 and Grasshopper version 0.9.0076.

## Downloading SRTM files for use in Grasshopper

DTM uses SRTM (Shuttle Radar Topography Mission) files in ASCII (Esri Grid) or XYZ file format.

SRTM files can be downloaded viathe following links for locations worldwide:

*[OpenTopography](http://opentopo.sdsc.edu/raster?opentopoID=OTSRTM.082015.4326.1) provided by the San Diego Supercomputer Center.

![t20-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_20/t20-0.png)

Navigate to the map where you can select an area of data to process. Click the `Select a Region` button and draw a rectangle within the screen.

NOTE: You should keep your selection relatively small if you plan to use the highest resolution available.

In the dropdown menu for Data Output Formats, choose Arc ASCII Grid.

You will have to fill out a Job Description to submit your request for downloading. Your results will be processed and listed as a compressed raster.

*[CGIAR-CSI](http://srtm.csi.cgiar.org/selection/inputcoord.asp) provided by the Consortium for Spatial Information.

![t20-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_20/t20-1.png)

Make sure the Selection Server is set to `CGIAR-CSA (USA)`.

You can change the Data Selection Method. We will use `Multiple Selection` for this tutorial.

Select `ArcInfo ASCII` in the Select File Format option.

Click on the map on the grid in the region you wish to download. The grid cell will change to dark blue displaying your selection. When you have finished making your selection, select `Click here to Begin Search >>`.

![t20-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_20/t20-2.png)

The following page will preview your download scope. Click the green arrow next to `Data Download`. We will use the HTTP Data Download option for this tutorial.

## Importing Topography Data using DTM

Open a new Rhino files and load Grasshopper.

![t20-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_20/t20-3.png)

Create a `File Path` component. Right click and link to the ASCII file you downloaded online.

Create a `DTM `component and load the `File Path` ouput into the `esri` input of the `DTM` component. 

You can specify a boundary by drawing a rectangle in Rhino and referencing the rectangle using a `Curve` parameter and connecting it to the `rect` input of the `DTM` component. This reduces the area of the mesh so that your file will process faster.

You can adjust the resolution using the `res` input of the `DTM` component. Create a `Slider` with a domain from 0 to 1 and attach it to the `DTM` component. A resolution of 1 will be the highest resolution and may take long amounts of time to process if your area of interest is large.

You can now see your topography imported into Rhino as a mesh. You can create contours of this surface in Grasshopper to extract contour lines. These files are best used for topography at a resolution of 1/3 arcseconds or 10 meters.

