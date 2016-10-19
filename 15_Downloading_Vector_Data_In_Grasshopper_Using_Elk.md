# Downloading Vector Data in Grasshopper using Elk

This tutorial uses Elk version 2.2.2 available via [Food4Rhino](http://www.food4rhino.com/project/elk?ufh)

Several plug-ins available for Grasshopper enable the use of spatial data in Grasshopper via online sources. This tutorial will cover how to download vector data in Grasshopper using the Elk plug-in.

## Loading OSM Data using Elk

*IMPORTANT: This tutorial requires an internet connection*

![t15-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_15/t15-0.png)

Install the Elk plug in by copying all appropriate files into the Grasshopper Components folder, accessed in Grasshopper under `File` > `Special Folders` > `Component Folder`. You will have to unblock all `.dll` files and `.gha` files by right clicking on the file > `Properties` > `Unblock` at the bottom of the `General` tab. Now restart Grasshopper and a new tab for Elk will appear.

![t15-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_15/t15-1.png)

From the `Elk2` menu in the `Extra` tab in Grasshopper, load the `Location` component. The Location component is primarily for preprocessing all of the node or point data from the OSM export. It wants a file path to an OSM file as the input and will output OSMPoints, a Point3d with an OSM defined ID, the text string of the full XML file, and the latitude and longitude domains. We will need to download a OSM file.

![t15-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_15/t15-2.png)

Navigate to [OpenStreetMaps](https://www.openstreetmap.org/) to download the OSM file we need.

![t15-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_15/t15-3.png)

Zoom to your area of interest and select `Export` at the top left. In the left menu you can select `Manually select a different area` to draw a bounding rectangle on your map. Click `Export`. If the export fails, you can try one of the options in the left menu bar such as the Overpass API to download the data.

*NOTE: Since OSM data is open source data, the maps may have incompleteness in parts, but will suffice for most areas of interest.*

![t15-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_15/t15-4.png)

Set the `File Path` component to the source of your downloaded OSM data. Load a `OSM Data` component. Attach the `OSM` output from the `Location` component to the `O` input and attach the `File Path` to the `F` input. 

You will now see your data as points in the Rhino viewport. You can use a `Polyline` component to draw the lines between the points.

![t15-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_15/t15-6.png)

You can now right click on the OSM component to toggle different `Feature Types` from the dropdown menu.

![t15-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_15/t15-7.png)

You can continue to add data by copying creating different streams of OSM inputs with different `Feature Types`. The attributes of these `Feature Types` are found in the `K` ouput of the `OSM Data` component.

![t15-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_15/t15-8.png)

For some geographies, you can extrude buildings to their heights by right clicking on the `OSM Data` component and clicking on `Create 3D Buildings`. A `Bldg` output will be added and you can attach this output to a `Geometry` parameter. Your buildings will now be displayed in 3D.

The advantage to using Elk is the ability to convert OSM data in Grasshopper for display in Rhino, quickly selecting the feature types of your interest.