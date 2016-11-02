# Downloading Vector Data in Grasshopper using Heron

This tutorial uses Heron GHA version 0.2.0.0 available via [Food4Rhino](http://www.food4rhino.com/project/heron?ufh)

This tutorial uses Rhinoceros 5.0 and Grasshopper version 0.9.0076.

The advantage of using the Heron plug-in is the ability to download rich datasets including raster images, census data from the US Census Bereau and USGS data. The plug-in requires significant set up time and will become limited without an advanced knowledge of Grasshopper.

## Setting a Location in Heron

*IMPORTANT: This tutorial requires an internet connection*

![t16-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-0.png)

Install the Heron plug in by copying all appropriate files into the Grasshopper Components folder, accessed in Grasshopper under `File` > `Special Folders` > `Component Folder`. You will have to unblock all `.dll` files and `.gha` files by right clicking on the file > `Properties` > `Unblock` at the bottom of the `General` tab. Now restart Grasshopper and a new tab for Heron components will appear.

![t16-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-1.png)

Load the `RESTGeocode` component into the Grasshopper window. This panel will be used to make a search to establish our location. We will enter into a `Panel`, `Empire State Building, New York` and attach it to the `addresses` input of the `RESTGeocode` component. You can see the output data including the coordinates of latitude and longitude.

Now load a `Decimal Degrees to XY` component to make the transformation from coordinated of decimal degress to euclidean coordinates. Attach the `LAT` and `LON` input and outputs respectively.

You will be able to see a point in the Rhino viewport. You may have to scroll to find this point or bake it and use `Zoom Select` to find it easily.

Load a `Set EarthAnchorPoint` component. Add a boolean toggle to the `set` input and attach the coordinates respectively. This minimizes distortion during geographic transformation to Euclidean coordinates.

## Downloading Raster Imagery

![t16-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-2.png)

Create a curve in the Rhino viewport 1000 meters by 1000 meters centered around our Earth Anchor Point. Create a `Curve` parameter in Grasshopper and reference the curve.

Create a `RESTraster` component from the Heron Plugin. We will create value lists for data input. This will allow us to filter by our selections and make separate queries for our downloads.

Create a `Value List` parameter for the `resolution` input of the `RESTraster` component. Right click on the value list and click `Edit` to edit the Value List Constants.

Enter the following into the list:

```
None = 
Low  = 256
Med  = 512
High = 1024
Max  = 2048
```

Now create a panel for the `fileLocation` input of the `RESTraster` component. Write `C:\temp\` to store the file in the temporary location on your C Drive.

Create a panel for the prefix input of the `RESTraster` component. Write `aerial` to add the prefix to the file name.

Create a `Value List` parameter for the `URL` input of the `RESTraster` component. Right click on the value list and click `Edit` to edit the Value List Constants.

To query the Catalog of ESRI ArcGIS REST Basemaps, enter the following into the list:

```
World Imagery                   = "http://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/export?"
World Topographic               = "http://server.arcgisonline.com/ArcGIS/rest/services/World_Topo_Map/MapServer/export?"
World Physical Map              = "http://server.arcgisonline.com/ArcGIS/rest/services/World_Physical_Map/MapServer/export?"
World Street Map                = "http://server.arcgisonline.com/ArcGIS/rest/services/World_Street_Map/MapServer/export?"
World DeLorme Street Map        = "http://server.arcgisonline.com/ArcGIS/rest/services/Specialty/DeLorme_World_Base_Map/MapServer/export?"
```

To query the Catalog of ESRI ArcGIS REST Basemaps, enter the following into the list:

```
Ortho 1 Foot Imagery     = "http://raster.nationalmap.gov/arcgis/rest/services/Orthoimagery/USGS_EROS_Ortho_1Foot/ImageServer/exportImage?"
Ortho Imagery            = "http://raster.nationalmap.gov/arcgis/rest/services/Orthoimagery/USGS_EROS_Ortho/ImageServer/exportImage?"
NAIP Imagery             = "http://raster.nationalmap.gov/arcgis/rest/services/Orthoimagery/USGS_EROS_Ortho_NAIP/ImageServer/exportImage?"
Land Cover               = "http://raster.nationalmap.gov/arcgis/rest/services/LandCover/USGS_EROS_LandCover_NLCD/MapServer/export?"
Land Cover - Conus 01    = "http://raster.nationalmap.gov/arcgis/rest/services/LandCover/conus_01/MapServer/export?"
Land Cover - Conus 06    = "http://raster.nationalmap.gov/arcgis/rest/services/LandCover/conus_06/MapServer/export?"
Land Cover - Development = "http://raster.nationalmap.gov/arcgis/rest/services/LandCover/Development_0106/MapServer/export?"
Land Cover - Wetland     = "http://raster.nationalmap.gov/arcgis/rest/services/LandCover/Wetland_0106/MapServer/export?"
Topo - Scanned Maps      = "http://raster.nationalmap.gov/arcgis/rest/services/Scanned_Maps/USGS_EROS_DRG_SCALE/ImageServer/exportImage?"
```

Create a `Boolean Toggle` and set to true for the `get` input of the `RESTraster` component.

Create a `Boundary Surfaces` component and attach the `imageFrame` output to the `Edges` input.

Create a `SurfaceMapping` component and graft the `Mesh` input. Attach the boundary curve to the `Mesh` input and the `Surface` ouput of the `Boundary Surface` to the `Surface` input of the `SurfaceMapping component.

Finally, add a `Custom Preview Materials` component and attach the `Mapped Mesh` output of the `SurfaceMapping` component to the `G` geometry input. Attach the `Image` ouput of the `RESTraster` component to the `DB` diffuse bitmap input.

You will now see your image mapped within the boundary curve in the Rhino viewport. You can move your boundary curve and the script will automatically download new data for the region within the boundary.

![t16-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-3.png)

You can filter your selection in the `Value List` inputs you created to visualize different orthographic images, from aerial images to scanned topo maps.




