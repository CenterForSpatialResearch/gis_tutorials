# Network Analysis: Creating a Service Area 

This tutorial will use the [LION dataset](https://www1.nyc.gov/site/planning/data-maps/open-data/dwn-lion.page), a dataset of New York City's streets, [Libraries in New York City](https://data.cityofnewyork.us/Business/Library/p4pf-fyc4), and [borough boundaries (clipped to shoreline)](https://www1.nyc.gov/site/planning/data-maps/open-data/districts-download-metadata.page). This data is also available on the [X drive](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/21_Connecting_to_X_Drive.md). We will create a service area at a specified distance from libraries along New York City streets. Network analysis such as this is helpul for exploring the relationship between point features along polyline networks. 

## Getting Started 
Open up ArcMap and make sure that the 'Network Analyst' extension is enabled by going to Customize --> Extensions. Check the Network Analyst option. 
![t28-0.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-0.png)

Next, add the LION, borough boundaries and libraries shapefiles. Note: to change a layer name, simply 'click' on the layer or go to the 'General' tab under 'Properties'. When adding the LION file, double click the 'lion folder' and then the 'lion.gdb' geodatabase and then select the 'lion' line file.
![t28-1.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-1.png)

## Setting up data
To create a service area of a half-mile walking distance from libraries, we first need to isolate pedestrian streets from the LION shapefile. To do this, we will be using the LION [metadata](https://www1.nyc.gov/assets/planning/download/pdf/data-maps/open-data/lion_metadata.pdf?r=17c) to figure out what attributes correspond to this. The 'NonPed' field delineates between streets that are pedestrian-accessible or not, and the 'TrafDir' field delineates types of streets, including pedestrian paths. 
![t28-2.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-2.png)
![t28-3.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-3.png)

To isolate only pedestrian streets, we will first select all features with a 'blank' value for the 'TrafDir' field using 'Select by Attributes'. Right click on the 'lion' layer and select 'Open attribute table'. The 'Select by Attributes' button is the third from the left at the top of the attribute table. Click on that, and find 'TrafDir' in the field names. Double click on it, and either type or select '<>' to select features that the TrafDir field is 'not equal to'. Click the 'Get Unique Values' button to populate the window with the values of the TrafDir field, and doubleckick '''' for the blank values. Hit 'apply'.
![t28-4.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-4.png)
![t28-5.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-5.png)

Next, we will add to our selection by changing the selection in the dropdown menu at the top of the attribute table to 'select from current selection'.

![t28-6.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-6.png)

This time, we will be adding to our previous query. Click 'And', select 'NonPed' as the field and click 'Get Unique Values'. Finally, select '<>' and ''V'' to finish off the query. Basically, we are selecting streets that are accessible to pedestrians from our previous selection of all streets except non-street features. Finally, go through the same process to select street types that are NOT the ferry ( FeatureTyp <> 'F') from our current selection.Hit 'apply' and 'close'.
![t28-7.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-7.png)
![t28-8.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-8.png)

To make this selection a new layer, rightclick on the 'lion' layer name and scroll down to 'Data'. Select the 'Export Data' option, and 'save' after you choose where you want your file to be saved. Add the new, pedestrian only LION data to the map.
![t28-9.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-9.png)
![t28-10.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-10.png)

## Creating service area
*While we will be using points to create a service area, it is important to note that polygon features cannot be used to create service areas as is. A suitable alternative is using the centroid of these features, and you can get this by using the 'Feature to Point' tool in ArcToolbox under Data Management Tools --> Features. You can then use these points to calculate a service area.*

First, we will need to create a 'feature dataset' from our library points. Launch 'ArcCatalog' and navigate to the folder you are using for this analysis by clicking the 'Connect to Folder' button on top of the window.
![t28-11.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-11.png)

Create a new 'File Geodatabase' by rightclicking anywhere in the window with your files, and doubleclick that geodatabase. Rightclick in the window again and create a new 'Feature Dataset'. Name it as you wish, select the coordinate system, and keep the other options as default. 
![t28-12.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-12.png)
![t28-13.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-13.png)
![t28-14.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-14.png)
![t28-15.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-15.png)
![t28-16.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-16.png)
![t28-17.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-17.png)

Next, we will create a 'Network Dataset' (which is what we will use to calculate the relationship between the two layers). Doubleclick the feature dataset you just created to go into that folder, right click in the window and 'import' a new 'Feature Class (single)'. In the window that pops up, select the pedestrian streets shapefile we created earlier as the input feature and name your output feature class. There is no need to change the location of the output dataset because it is automatically set to the Feature Dataset we just created. Click ok. 
![t28-18.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-18.png)
![t28-19.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-19.png)

When the feature class has been created, rightclick in the window and create a new 'Network Dataset'. Most of the features remain defult, but make sure that 'None' is selected for how to model the elevation of your network features, 'RoadClass' is removed from attributes for the network dataset, 'No' is selected for establishing driving direction settings, and 'Build Service Area Index' is checked. Select 'Yes' when a window pops up asking if you would like to build the new network dataset.
![t28-20.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-20.png)
![t28-21.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-21.png)
![t28-22.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-22.png)
![t28-23.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-23.png)
![t28-24.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-24.png)
![t28-25.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-25.png)
![t28-26.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-26.png)
![t28-27.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-27.png)
![t28-28.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-28.png)
![t28-29.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-29.png)
![t28-30.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-30.png)

When the network dataset has been created, close ArcCatalog and return to ArcMap. Add the network dataset to the map by clicking the 'Add Data' button as was done before. You only actually need the file with the _ND attached to the end, but we can add all files in the network dataset to look at their relationships.
![t28-31.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-31.png)

Next, we can make the service area layer by going to ArcToolbox --> Network Analst Tools --> Analysis --> Make Service Area Layer. The 'default break values' indicate the extent of the service areas calculated. This is done in feet because the projected coordinate system of the layer is in feet (you can check by going to layer properties and going to the 'coordinate system' tab). So here 1320 and 2640 (ft) break values correspond to a quarter mile and half mile. 
![t28-32.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-32.png)
![t28-33.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-33.png)

To 'add the library locations to the service area' (in order for them to be used for the analysis), go to ArcToolbox --> Network Analst Tools --> Analysis --> Add Locations. 'Service Area' should be the Input Network Analysis Layer, and 'library' (or your point file) should be the Input Locations. 
![t28-34.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-34.png)
![t28-35.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-35.png)
![t28-36.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-36.png)

Finally, we can calculate the service area by rightclicking on the 'Service Area' layer and selecting 'Solve'. This essentially calculates distances (the break values) from the library locations along pedestrian streets instead of just creating a uniform buffer at specified distances.
![t28-37.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-37.png)
![t28-38.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-38.png)

These service area polygons are temporary, so we have to export the data by rightclicking on the 'Polygons' layer and selecting 'export Data'. 
![t28-39.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_28/t28-39.png)
