# Downloading Vector Data in Grasshopper using Mosquito

This tutorial uses Mosquito version 0.4c available via [Studio Smuts](http://www.studiosmuts.com/ceed3/mosquito/

Several plug-ins available for Grasshopper enable the use of spatial data in Grasshopper via online sources.

## Downloading Vector Maps

*IMPORTANT: This tutorial requires an internet connection.*

![t12-0.png](URL)

Load the `Location` component. Add a panel where you can add the input location. You can simply search for a place, such as `New York City` or an address, such as `116 St. & Broadway, New York, NY 10027`. We will type in `Columbia University` into our panel.

![t12-1.png](URL)

Plug in the panel into the `Location` input of the `Location` component. Using a `List Index` component to extract only one point and add the output `Points` to the `List` input. Add a `Circle` component with center around the `List Index` output `index`. These circles define the scope of our search in the `Vector Maps` component.

![t12-2.png](URL)

Add a `Number Slider` component with a value of 0.01 for the radius of the circle. Connect the slider to the `radius` input of the `Circle` component.

*IMPORTANT: The radius of this circle must not be too large or the download request may be rejected. We will use a radius of 0.01*

![t12-3.png](URL)

You may need to zoon in to see your circle and point.

![t12-4.png](URL)

Create a `Vector Maps` component. Connect the `Circle` component output to the `Area` input of the `Vector Maps` component.

![t12-5.png](URL)

Click the `Reload` button on the component. The component will display a loading and downloading preview until completed.

![t12-6.png](URL)

Basic roads will now be visible in the Rhino viewport.

## Downloading Additional Information

![t12-7.png](URL)

Create a `Boolean Toggle` component and connect to `AllRoads` and `Buildings` in the `Vector Maps` component. Click `Reload`. The process may take few minutes.

To download height information for creating 3D buildings add an `Extrude` component and connect the `BuildingLines` to the `B` input.

Connect the `BuildingHeights` output to a `Unit Z` component and connect the `vector` output to the `direction` input of the Extrude component. Finally, cap the breps using the `Cap` component to close all extruded surfaces.

![t12-8.png](URL)

You will now have buildings extruded to appropriate heights and roads displayed once baked into Rhino.