## Fixing Broken Layer Source Links in ArcGIS

*Tutorial created by Jonathan Izen (jai2125@columbia.edu)*

This tutorial will guide you through the process of fixing broken layer source links in ArcGIS.

ArcGIS does not embed or import data layers into each individual project file. Instead, it creates links from the project to the data layers. As a result, as files are moved or renamed, these links occasionally need to be repaired.

#Identifying a Broken Link

![t4-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_04/t4_1.PNG)

If a data layer does not appear in the map viewport, you probably have a broken link. This is noted in the `Table on Contents` by a RED EXCLAMATION POINT beside the layer name. Note that the check-box that normally shows whether a layer is visible is greyed out, because ArcMap cannot find or access the file to turn it on.

#Identifying and Fixing Link Paths

![t4-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_04/t4_2.PNG)

Usually, it is helpful to know the path that ArcMap is following to find the data file. You can find it in the `Layer Properties`. First, Right-Click on the layer name in the `Table of Contents`, then select `Properties`. The `Layer Properties` dialogue box will appear. Choose the `Source` tab.

The last known path for the data layer is displayed after `Location` in the `Data Source` box.

![t4-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_04/t4_4.png)

You can reset the data source (i.e. create a new path and fix the broken link) by clicking the `Set Data Source` button on the lower right. (Note: You can short-cut to resetting the data source by double-clicking on the red exclamation point next to the data layer's name in the `Table of Contents`.)

The dialogue below (`Data Source`) will appear. Navigate to your data file and click `Add`. Click `OK` in the `Layer Properties` dialogue box.

![t4-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_04/t4_5.PNG)

Your broken link should now be repaired, and your data layer should now be visible in your map project.

![t4-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_04/t4_6.PNG)

It is good practice to save your map while storing relative pathnames to data sources. To do so, go to `File` > `Map Document Properties`. Make sure the checkbox near the bottom for `Pathnames` is checked, asking if you want to store relative pathnames to data sources. If this is enabled, the next time you save your map, the links to the data layers will be preserved.