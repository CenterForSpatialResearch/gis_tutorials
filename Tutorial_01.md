## Creating a Basic Map in ArcMap

*Tutorial created by Jonathan Izen (jai2125@columbia.edu)*

This tutorial will cover some basics of the ArcMap user interface, using map symbology, and creating a map layout.

![t1-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_1.PNG)

* Open ArcMap. Go to `Start` > `Programs` > `ArcGIS` > `ArcMap`. A dialogue box should appear, as below. To start a new map project, select `Blank Map` and click `OK`.

![t1-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_2.PNG)

* To Add Data to the map project, click on the `Add Data` button on the toolbar, shown below. A dialogue will appear, allowing you to navigate to the data files you want to add as layers of your map.

![t1-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_3.PNG)

* Once you have added data, you can zoom and pan using the buttons on the toolbar. Select tools allow you to make selections from the data features. The `identify` tool allows you to query individual features for their attribute data.

![t1-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_4.PNG)

* You can arrange the ordering of the layers by stacking the data layer names in the `Display` tab of the `Table of Contents` on the left of the screen. The ordering of the layers in the `Table of Contents` will correspond to their ordering in the map. Below is an example. The open space layer is displayed above the building layer, which is in turn displayed above the water layer.

![t1-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_5.PNG)

* To change the symbology of your layers, right-click on the layer name and choose `Properties`.

![t1-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_6.PNG)

A dialogue will appear. Under the `Symbology` tab, you will find the options for coloring or visualizing your data.

Option A: To keep all features a single color, choose `Features` > `Single Symbol` on the left. You can change the color by clicking on the swatch.

![t1-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_7.PNG)

Option B: To visualize your data based on a qualitative category, choose `Categories` on the left and specify (by clicking) the type of categorization. In the image below `Unique Values` is chosen.

![t1-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_8.PNG)

In the `Value Field` drop down menu, select the field by which you'd like to visualize your data. In the image above, the school district field was chosen. Click `Add All Values` to display the category values. You can change the color of your symbols by either using the Color Ramp drop-drop down menu or double-clicking on the swatches to the left of the `Values` list.

Option C: To visualize your data based on numeric quantities, select `Quantities` on the left and specify (by clicking) the type of visualization. In the image below, `Graduated Colors` is chosen.

![t1-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_9.PNG)

In the `Value` drop-down menu, select the field by which you'd like to visualize your data. If appropriate, you can normalize your data by another quantity field by selecting it from the `Normalization` drop-down. You can change the color of your symbols by either using the Color Ramp drop-down menu or by double-clicking on the swatches on the left of the `Range` list.

To change the number of displayed value ranges, you can select the number of classes from the `Classes` drop-down menu. By default, 5 classes are displayed and delineated using Jenks Natural Breaks algorithm. If you want to change this default, you can click on the `Classify…` button. A dialogue appears as below.

Again, you can change the number of classes by using the `Classes` drop-down menu. You can change the method of classification by using the `Method` drop-down. Your options include manually classifying your data, equal interval, and standard deviation classification as well as some others. The histogram displays the distribution of your data, with blue vertical lines showing the breaks between classes. To manually classify the dataset, you can either move the blue break lines (by clicking and dragging them) or typing in the Break Values in the list to the right of the dialogue. On the upper right corner of the dialogue box, basic statistics corresponding to the data is displayed that can be useful in deciding how to visualize your data.

In all cases, clicking `OK` will save and display your new symbology.

## Laying Out and Exporting Your Map:

![t1-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_10.PNG)

* To create a map layout, switch your view from `Data View` to `Layout View` by clicking on the icon of a page in the lower left corner of the map window as below.

![t1-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_11.PNG)

The map window should now show you your map's data frame on a sheet of paper. You can adjust the size and location of the data frame by adjusting its bounding box.

A new set of tools to zoom and pan appears when you are in the `Layout View`. The `Data View` zoom and pan tools are still active and will affect the map within the data frame. To zoom and pan on the page without affecting the map, use the (page) `Zoom` and `Pan` toolbar shown above.

![t1-12.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_12.PNG)

* You can add standard elements to your map through the `Insert` menu shown below. The `Legend`, `North Arrow`, `Scale Bar`, and `Scale Text` options each lead to dialogues that allow you to customize those map elements.

![t1-13.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_13.PNG)

You can change the position the elements you inserted into the page area.

![t1-14.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_01/t1_14.PNG)

* When you are finished with your map, you can export it to a variety of formats. Go to `File` > `Export Map…` to reach a dialogue box where you can choose your export format and save your map. You will find that you can export your map as an image file (i.e. JPG) for immediate use or as a vector-based file (i.e. EPS) for further graphics editing.
