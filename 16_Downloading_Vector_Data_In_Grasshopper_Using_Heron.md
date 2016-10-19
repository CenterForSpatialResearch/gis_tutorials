# Downloading Vector Data in Grasshopper using Heron

This tutorial uses Heron GHA version 0.2.0.0 available via [Food4Rhino](http://www.food4rhino.com/project/heron?ufh)

Several plug-ins available for Grasshopper enable the use of spatial data in Grasshopper via online sources. This tutorial will cover how to download vector data in Grasshopper using the Heron plug-in.

## Loading GIS Data using Heron

*IMPORTANT: This tutorial requires an internet connection*

![t16-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-0.png)

Install the Heron plug in by copying all appropriate files into the Grasshopper Components folder, accessed in Grasshopper under `File` > `Special Folders` > `Component Folder`. You will have to unblock all `.dll` files and `.gha` files by right clicking on the file > `Properties` > `Unblock` at the bottom of the `General` tab. Now restart Grasshopper and a new tab for Heron components will appear.

![t16-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-1.png)

Load the `RESTGeocode` component into the Grasshopper window. This panel will be used to make a search to establish our location. We will enter into a `Panel`, `Empire State Building, New York` and attach it to the `addresses` input of the `RESTGeocode` component. You can see the output data including the coordinates of latitude and longitude.

![t16-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-2.png)

Now load a `Decimal Degrees to XY` component to make the transformation from coordinated of decimal degress to euclidean coordinates. Attach the `LAT` and `LON` input and outputs respectively.

![t16-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_16/t16-2.png)

Load a `Set EarthAnchorPoint` component. Add a boolean toggle to the `set` input and attach the coordinates respectively. This minimizes distortion during geographic transformation to Euclidean coordinates.