# Downloading Spatial Data in Grasshopper using Heron

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

Heron enables the ability to quickly download raster imagery from online sources for display directly into Rhino via Grasshopper.

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

To query the Catalog of USGS Basemaps, enter the following into the list:

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

## Downloading Vector Data

Heron enables the ability to download vector data from online sources directly into Rhino via Grasshopper. We will download census data from the US Census Bureau and visualize their attributes.

*NOTE: You can only download up to 10 vectors at a time in Heron for each query. To select more vectors you will have to build a Grasshopper script with multiple queries.*

![t16-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-4.png)

First we will set up a query to download the data. Create a `Value List` component. For this tutorial we will download ESRI demographic data.

To query the Catalog of ESRI Demographic Data enter the following into the list:

```
USA 1990-2000 Population Change    = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_1990-2000_Population_Change/MapServer/"
USA 2000-2010 Population Change    = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_2000-2010_Population_Change/MapServer/"
USA Average Household Size         = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Average_Household_Size/MapServer/"
USA Diversity Index                = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Diversity_Index/MapServer/"
USA Labor Force Participation Rate = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Labor_Force_Participation_Rate/MapServer"
USA Median Age                     = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Median_Age/MapServer/"
USA Median Home Value              = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Median_Home_Value/MapServer/"
USA Median Household Income        = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Median_Household_Income/MapServer/"
USA Median Net Worth               = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Median_Net_Worth/MapServer/"
USA Owner Occupied Housing         = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Owner_Occupied_Housing/MapServer/"
USA Percent Over 64                = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Percent_Over_64/MapServer/"
USA Percent Under 18               = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Percent_Under_18/MapServer/"
USA Population by Sex              = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Population_by_Sex/MapServer/"
USA Population Density             = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Population_Density/MapServer"
USA Projected Population Change    = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Projected_Population_Change/MapServer/"
USA Recent Population Change       = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Recent_Population_Change/MapServer/"
USA Retail Spending Potential      = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Retail_Spending_Potential/MapServer/"
USA Social Vulnerability Index     = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Social_Vulnerability_Index/MapServer/"
USA Tapestry                       = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Tapestry/MapServer/"
USA Unemployment Rate              = "http://services.arcgisonline.com/arcgis/rest/services/Demographics/USA_Unemployment_Rate/MapServer/"
```

You will now be able to query these sources using the `Value List` component. Create a `Text Parameter` and connect the output of the `Value List` to the input of the parameter. You can rename this text parameter `URL to Query`.

Now create a `RESTLayer` Component`. You can attach a panel to the `mapDescription` output to describe the data source. Create a `Item Selector` component and attach the `mapLayers` output to the input of the component. This will allow you to toggle different layers available from each source (i.e. selecting by geography such of census data such as Block Groups, Tracts, Counties, and States). We will select `Tracts` for this exercise. Create a `Match Text` component and attach the `mapLayers` output to the `T` Text to Match input. Attach the output of the `Item Selector` of the Map Layers to the `P` Pattern input. Create a `Cull Pattern` component and attach the `M` match output of the `Match Text` component to the `P` Pattern input. Finally, attach the `mapIndex` output of the `RESTLayer` output to the `L` List input of the `Cull Pattern` component.

To complete our query, we will create a `Layer URL` component. Attach the `URL to Query` text parameter you created to the `x` input. Attach the `L` output of the `Cull Pattern` component to the `y` input. Our query is now expressed in the `r` result output of the component.

![t16-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-5.png)

Create a `RESTVector` component. This component will use out query to download vector data from the source. We will reference our original `Curve` parameter centered around our Earth Anchor Point from the first example. Attach this parameter to the `boundary` input of the `RESTVector` component. Attach the query we built and using a `Text` parameter to the `URL` input of the `RESTVector` component. Create a `Boolean Toggle` and connect to the `get` input to update vectors if you change your query.

This component will download the vector data as points. Create a `Polyline` component and attach the `featurePoints` output of the `RESTVector` component to the `V` Vertices input. This will convert the points to polylines. You can create `Panels` and attach them to the `fieldNames` and `fieldValues` to preview the attributes of the downloaded vector data.

To visualize the data we can build a query using the fields to create a color ramp. Attach the `fieldNames` to an `Item Selector` to query a specific field. Use a `Text Match` component and attach the `Item Selector` with the selected attribute to the `P` Pattern input. Attach the `fieldNames` to the `T` Text to Match parameter. Create a `Cull Pattern` component and attach the `M` Match ouput of the `Text Match` component to the `P` Pattern input. Attach the `fieldValues` output of the `RESTVector` component to the `L` List input. This will select the appropriate field values using a selected field name.

We will now define the domain of the attributes and convert them into a color ramp. Create a `Bounds` component and attach the `L` List output of the `Cull Pattern` component to the `N` Numbers input, flattening the input. Create a `Deconstruct Domain` component and attach the `I` Domain ouput of the Bounds to the `I` Domain input. Create a `Gradient` and attach the `S` Start and `E` End to the `L0` Lower Limit and `L1` upper limit, respectively. Attach the `L` output of the `Cull Pattern` component to the `t` Parameter input of the `Gradient`.

We must now convert our polylines to meshes to use visualize our `Gradient`. Convert the `Polylines` to `Boundary Surfaces`. Then use a `Mesh Brep` component to convert the `Boundary Surfaces` to Meshes.

Create a `Custom Preview Materials` component. Attach the `M` Mesh output to the `G` Geometry input of the `Custom Preview Materials`. Attach the `Gradient` output to the 

![t16-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-6.png)

Your vector data is now symbolized by the given attributes in the field you selected.
