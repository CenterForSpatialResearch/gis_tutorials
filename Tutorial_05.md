## Using Bluesky Aerial Orthophotos

*Tutorial created by Jonathan Izen (jai2125@colubia.edu)*

Below are intructions on how to use the 2003 Bluesky Orthophoto aerial photographs of New York City.

#The Map Projection

The Bluesky orthophotos are only georeferenced to the HARN projection. The first step in using these images is to change the projection of your map project to the appropriate projection.

In an empty ArcMap project, right-click in the map area of ArcMap and select `Data Frame Properties`. Under the `Coordinate System` tab, open the `Predefined` folder and navigate to `Projected Coordinate Systems` > `State Plane` > `NAD 1983 HARN (Feet, Intl, and US)` > `NAD 1983 HARN StatePlane New York Long Island FIPS 3104 Feet`. Highlight this projection. Click `OK`. Your map should now be projected to the same projection as the Bluesky files.

#The Borough Ortho Index .shp file

In ArcCatalog, copy the Index Shapefile for your borough of interest to your workspace. These files are found in the counties' folders in `X:\New_York_City\Base_Data\AERIALS\bluesky_orthophoto`. They are named `[county name]_ortho_index.shp`. (The index files are the only `.shp` files in the folders.) These indeces are the most convenient method of determining which of the many photo .jpg files cover your area of interest.

Add your copied shapefile to an ArcMap project. Once you have the index shapefile in ArcMap, identify which tiles cover your area of interest. You can do this by overlaying the index shapefile on another file of your area. Record the image ID number of the appropriate tiles. (This number is recorded under `IMG_ID` in the attribute table.) You can do this by labeling the features and zooming in to read the Image ID or by using the Information tool.

The Aerial .jpg Files

The `Image ID` numbers correspond to the .jpg files also found in the counties folders in `X:\New_York_City\Base_Data\AERIALS\bluesky_orthophoto`. Once you have identified the images you need, copy them to your workspace in ArcCatalog.

#Correcting the Spatial Reference

If you followed section 0 - The Map Projection, then this step should not be necessary. If, however, the image files are not located properly then this should fix the problem.

The images you have copied may not have a spatial reference. Add the .jpg file to your existing ArcMap project. If you are prompted with a warning that states your file does not have a spatial reference, click `OK`. You will have to correct the file's spatial projection. If you are not prompted with a spatial reference warning, then the image should appear in its proper place in the tiled grid, and the file you have copied is ready for you to use.

To correct the spatial reference:

* Remove the file from your ArcMap project.

* In ArcCatalog, navigate to your copied .jpg raster file. Right-click on the file name and select `Properties`.

* Scroll to `Spatial Reference` and click `Edit`.

* Click `Import,` then navigate to the `Ortho_Index` shapefile you copied. Select the `ortho_index` file, and click `Add`. This will assign your raster .jpg file the same spatial reference as the shapefile.

*Click `OK` to the remaining dialogue boxes.

* Add the .jpg raster to your ArcMap project. It should now fit neatly into the index shapefile, and be ready for your use.