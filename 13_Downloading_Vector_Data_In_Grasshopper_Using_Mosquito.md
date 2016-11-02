# Downloading Vector Data in Grasshopper using Mosquito

This tutorial uses Mosquito version 0.4c available via [Studio Smuts](http://www.studiosmuts.com/ceed3/mosquito/)
You will also need [Grasshopper](http://www.grasshopper3d.com/) for Rhino 5.0

The advantage of using Mosquito is the ability to download OpenStreetMap building footprints and roads directly through Grasshopper and easily extrude 3D buildings. Since OpenStreetMap data is open source data, the maps may have incompleteness in parts, but will suffice for most areas of interest. The plug-in has limited 3D capabilities beyond building extrusions but includes attributes for selected data.

## Downloading Vector Maps

*IMPORTANT: This tutorial requires an internet connection.*

![t13-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-0.png)

Install the Mosquito plug in by copying all appropriate files into the Grasshopper Components folder, accessed in Grasshopper under `File` > `Special Folders` > `Component Folder`. You may need to unblock the `Newtosoft.Json.dll` file and the `.DS_Store` file by right clicking on the file > `Properties` > `Unblock` at the bottom of the `General` tab. Now restart Grasshopper and a new tab for Mosquito components should be displayed.

![t13-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-1.png)

Load the `Location` component. Add a panel where you can add the input location. You can simply search for a place, such as `New York City` or an address, such as `116 St. & Broadway, New York, NY 10027`. We will type in `Columbia University New York City` into our panel.

![t13-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-2.png)

Plug in the panel into the `Location` input of the `Location` component. Using a `List Item` component to extract only one point and add the output `Points` to the `List` input. Add a `Circle` component with center around the `List Item` output `index`. These circles define the scope of our search in the `Vector Maps` component.

Add a `Number Slider` component with a value of 0.01 for the radius of the circle. Connect the slider to the `radius` input of the `Circle` component.

*IMPORTANT: The radius of this circle must not be too large or the download request may be rejected. We will use a radius of 0.01*

![t13-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-3.png)

You may need to zoom in to see your circle and point.

![t13-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-4.png)

Create a `Vector Maps` component. Connect the `Circle` component output to the `Area` input of the `Vector Maps` component.

Click the `Reload` button on the component. The component will display a loading and downloading preview until completed. Basic roads will now be visible in the Rhino viewport.

## Downloading Additional Road and Building Information

![t13-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-5.png)

Create a `Boolean Toggle` component and connect to `AllRoads` and `Buildings` in the `Vector Maps` component. Click `Reload`. The process may take few minutes.

## Projecting to Meters

![t13-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-6.png)

Create a `Boolean Toggle` component and attach it to the inputs `Reproject` and `CenterToWorld`. Set the boolean to true and `Reload` the `Vector Maps` component.

The map will now appear less distorted in the Rhino viewport.

## Extruding 3D Buildings

Depending on the location of your map, you may be able to extract height information for some cities such as New York City.

![t13-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-7.png)

To download height information for creating 3D buildings add an `Extrude` component and connect the `BuildingLines` to the `B` input.

Connect the `BuildingHeights` output to a `Unit Z` component and connect the `vector` output to the `direction` input of the Extrude component. Finally, cap the breps using the `Cap` component to close all extruded surfaces.

![t13-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-8.png)

You will now have buildings extruded to appropriate heights and roads displayed.

![t13-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_13/t13-9.png)

Finally, bake your geometry into Rhino.