## Data Types and 311 Data - ArcGIS

This tutorial will show you how to download 311 data for New York City and how to create a categorical and a quantitative map of this data. There are three basic steps in this process: first, select, filter and download 311 data; second, add the 311 data to a map in ArcMap; and third, classify the data so that it is correctly displayed on the map. In addition, this tutorial will also describe how to join the 311 data to another spatial dataset (census block groups) in order to aggregate it and display it based on its geographical location.

### Datasets:
The main dataset we will be using in this tutorial is based on 311 data. For those of you who don't know, 311 is a service provided by the city of New York where people can call in (dialing 311) and submit complaints or ask questions about living in the city (the service also accepts complaints online). Some of the most popular complaints filed through 311 are about parking, noise, garbage, rodents, dead or damaged trees, air quality, construction permits, graffiti, homelessness, street conditions, taxis and water quality. There are other categories and each one of these has it's own subcategories. Furthermore, each entry in the dataset comes with the following fields (amongst others):
* Created date
* Closed date
* Agency
* Complaint type
* Descriptor
* Location type
* Incident zip code
* Incident address
* Street name
* City
* Landmark
* Facility type
* Status
* Due date
* Resolution description
* Community board
* X and Y coordinates
* Latitude and longitude

As you can see, the dataset is very interesting and a great resource for anyone studying New York. **Nevertheless, a word of caution is necessary**: many people use this dataset to describe and analyze conditions in New York; however, the 311 data doesn't describe the city, it describes the complaints people file, it is not about the city, it is about the complaints, and even though the complaints might tell us something about the city, the distinction is crucial. Every dataset has its own biases and the 311 dataset has very strong ones: it collects data ONLY about the people who complain and ONLY about what they choose to complain about. Again, this dataset is much more about the complaints and the people who complain than about the conditions in the city. There is no 1 to 1 relationship between the 311 complaints and the conditions in the ground. That being said, though, it is still a great resource and very fun to play with. You can find out more about the 311 service [here](http://www1.nyc.gov/311/).

Other datasets we will be using are:
* nybb - New York City boroughs. Originally downloaded from [here](http://www.nyc.gov/html/dcp/html/bytes/districts_download_metadata.shtml).
* HYDRO - New York hydrography. Originally downloaded [here](https://data.cityofnewyork.us/Environment/Hydrography/drh3-e2fd).
* hydropol - U.S. Hydrographic features. Originally downloaded from [here](http://www.rita.dot.gov/bts/sites/rita.dot.gov.bts/files/publications/national_transportation_atlas_database/2014/polygon).
* tl_2015_36_bg - New York State census block groups. Originally downloaded from [here](https://www.census.gov/cgi-bin/geo/shapefiles/index.php). Here you should download the census block groups for New York state for 2015.
* state - U.S. State Boundaries. Originally downloaded from [here](http://www.rita.dot.gov/bts/sites/rita.dot.gov.bts/files/publications/national_transportation_atlas_database/2014/polygon)

### Creating Noise Maps of 311 Data in New York City
#### Downloading 311 Data
The first step in this tutorial is to select, filter and download the 311 data. The [NYC Open Data portal](https://nycopendata.socrata.com/) is a great resource for data related to New York City and it provides an easy way of accessing 311 data. In it's search bar type "311" and it should take you to a list of datasets related to 311 data. The one we are looking for is called "311 Service Requests from 2010 to Present". Alternatively, you might see a big yellow icon at the top of this page related to 311; this will also take you to the dataset. Open the "311 Service Requests from 2010 to Present" and then click on `view data` at the top of the page.

Once you've accessed the dataset you will see something like this:

![311 Dataset](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/01_311_Dataset.png)
Here, we need to filter the database to download only the records regarding noise complaints for the first 6 months of 2016. You could attempt to download records for a longer period of time, but the files might get too large. To filter the data do the following:
* On the right-hand panel, where it says "Filter", create a small query with the drop-down menus. Where it says `Unique Key`, change it to `Complaint Type`. Keep the `is` and then type in "Noise" in the space below (The query should read 'Complaint type is noise'. Make sure there is a check-mark next to the word 'Noise'. You will see how the dataset is filtered and you only get the complaints of type 'Noise'.
* Next, click on `Add a New Filter Condition` and create another query that reads `Created Date` `is between` "01/1/2017 12:00:00 AM" and "07/1/2017 12:00:00 AM".
You should now see the data only for 'Noise' complaints created between the start of 2017 and the end of June 2017.
* Your filters should look something like this:

![311 Filters](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/02_Filters.png)
* Finally, click on the `Export` button at the top right-hand corner of the site and choose the `CSV` format. Your file should start downloading then.
* If you open your .csv file in Excel you will see that there are about 25,000 records and that they have both X and Y coordinates and Latitude and Longitude. In the next steps we will use these fields to add the 311 data to an ArcMap map.

#### Adding CSV data to ArcMap
* First, open ArcMap and add the following layers:
  * nybb
  * Roadbed
  * HYDRO
  * hydropol
  * state
* Organize your layers so that you have the water for New York on top, then boroughs, then the water for the country and the last the states.
* Now, to add the CSV file we downloaded, click on the `Add Data` button on the top toolbar (the one with the `+` sign).
* In the menu that comes up, look for your .csv (311 data) file and add it to your map.
* Once you've added your data to the map you need to create points based on some of the fields in the data. Just to check, right-click on the 311_Service_Requests layer and choose `Open`, you should see the attribute table with the data. Notice that there are columns for `Latitude` and `Longitude` and towards the end two more for `X Coordinate (State Plane)` and `Y Coordinate (State Plane)`. We can use either one of these pairs to plot points on the map. The difference is the projection these coordinates use: the first one uses WGS 1984 and the second one uses the State Plane coordinate reference system. For the purposes of this tutorial we will use latitude and longitude, but note that either one is fine, as long as you specify the corresponding coordinate reference system when you are plotting the points (in the next step). Close the attribute table.
* Now, to actually plot points on the map do the following:
  * Right-click again on the 311 layer and select `Display XY Data...`.

  ![Display XY Data](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/04_DisplayXY.png)
  * In the menu that appears, choose the fields for the X and the Y: `Longitude` for X and `Latitude` for Y.
  * Finally, in the bottom part, click on `Edit` to choose the right coordinate system for this data.
  * In the sub-menu that appears, navigate to the `Geographic Coordinate Systems` folder, in there open the `World` folder and choose `WGS 1984` as your coordinate system. Click `OK`.

  ![Coordinate System](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/04_CoordinateSystem.png)
  * Your final menu should look like this; make sure you've selected the right fields and the right coordinate system.

  ![Display XY Menu](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/04_DisplayXY_Menu.png)
  * Once you click `OK` you will be asked if you want to add an `Object-ID Field` to the data, say `OK`.
  * Your points should now be displayed.
* Even though your points are already on the map, this is just a temporary layer. If you remove the layer, you will need to go through the whole importing process to add them again. To avoid this, we need to export the layer as a shapefile:
  * Right-click on the new 311 layer (the one that has the points, not the .csv table) and select `Data` and `Export Data...`
  * In the menu choose the location where you will save your new shapefile and make sure your `Save as type:` is `shapefile`.
  * And in the main export menu, make sure that under `Use the same coordinate system as:` you select `the data frame` so that the new shapefile takes the same coordinate system as your map (which, if you added the boroughs as your first layer, should have the State Plane coordinate system).
  * Once you export your layer, click `Yes` to add it to your map and then remove the original one and the temporary point one by right-clicking and choosing `Remove`.

#### Symbolizing the Data
The last step in creating a qualitative map of the 311 data is a simple one: we need to symbolize each complaint using its subcategory.
* Right-click on the 311_Data layer and choose `Properties`.
* Go to the `Symbology` tab.
* Since we will symbolize the data based on **categorical data** choose `Categories` on the left-hand panel and under `Value Field` choose `Descriptor` (this is the field that holds the subcategories of the noise complaints).
* Now click on `Add All Values` at the bottom of the window. ArcMap will go through the data and select each individual category.
* Lastly, you should change the appearance of the dots: adjust their size, stroke and fill color like you did for the land use map.
* Your window should look something like this:

![Symbology](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/05_Symbology.png)
* Once you've adjusted that, click 'OK'.
* Finally, you need to change the appearance of the other layers, add a scale bar, legend, title, source and brief description, and export your map as a PDF file.

![Final Map](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/05_FinalMap.png)

#### Creating a Quantitative Map of 311 Data
Let's say you want to identify which census block group has the highest number of 311 noise complaints. To do this, you first have to join your 311 data to a layer containing the boundaries of New York City's census block groups.
* First, add the census block group shapefile (tl_2015_36_bg) you downloaded from the census website.
* Move this layer so that it's located below the HYDRO layer.
* If you zoom out, you will notice that this layer includes the census block groups for the whole State. However, we only need the ones for New York City. To select just these block groups we will use the `select by attributes` method, which means selecting based on data in one of the fields of the layer. The census block group layer contains a field listing the specific county each block group is located in; we will use this field to select only the census block groups located in any of the 5 counties that make up New York City:
  * First, right-click on the census block group layer and select `Open Attribute Table`. Here you will see the data associated with each of the census block groups. The second column, the one called `COUNTYFP`, contains the county identifiers, and this is the one we will use to select only the New York City block group.
  * Now we need to select all the census block groups that have as their COUNTYFP `005` (Bronx), `061` (Manhattan), `047` (Brooklyn), `081` (Queens) or `085` (Staten Island). Close the attribute table.
  * To select features based on attributes click on `Selection` and `Select by Attributes...` In this menu we will construct a query selecting only the features that have any of these numbers for their `COUNTYFP` value.

  ![Final Map](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/06_SelectByAttributes.png)

  * First, at the top, select the appropriate layer.
  * Then, double-click on the field that we will use ("COUNTYFP") to make it appear in the bottom panel.
  * Now type `=` so that it appears after the "COUNTYFP" in the bottom panel.
  * Now click on the `Get Unique Values` button so that the program displays all the possible values for that field. As we said above, we will select features where "COUNTYFP" is `005` or `061` or `047` or `081` or `085`.
  * Double-click on `005` to make is appear in the bottom panel.
  * Now, click on the `Or` button (or you can type it too), and then again on "COUNTYFP" and then the `=` sign and then the next number. Do this for all the numbers.
  * At the end, along with the text above this last panel you can read the query as if it was a phrase: `SELECT * FROM tl_2015_36_bg WHERE: "COUNTYFP" = '005' OR "COUNTYFP" = '061' OR "COUNTYFP" = '047' OR "COUNTYFP" = '081' OR "COUNTYFP" = '085'` (the `*` means all, so you are saying, select all the records where "COUNTYFP" is this, or that, or that...).
  * Before you click `OK`, click `Apply`. If all is fine, you should see the selected features highlighted in blue. If all the ones for New York City are highlighted, click `OK`.

  ![Final Map](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_23/06_Selection_Query.png)

  * Finally, to create a shapefile with only the selected features, right-click on the census block group layer and select `Save As...`. In the next menu choose the following settings:
    * Format: `ESRI Shapefile`
    * Save as: choose the right location and name your file 'NYC_BlkGrp'
    * CRS: `EPSG:102718 - NAD_1983_StatePlane_New_York_Long_Island_FIPS_3104_Feet`
    * Check `Save only selected features` - (this one is very important; if you don't check it you will just export a copy of your original layer with all the features, selected or not)
    * Uncheck `Skip attribute creation` - (you still want to retain the attributes associated with each point)
    * Check `Add saved file to map` - (so that once you export the layer, the layer is added to your map)
  * Click `OK` and you should see a new layer with only New York City block groups.
* Now we need to join the 311 data to the census block groups and get a count of how many complaints are in each block group. To do this, click on `Vector` `Analysis Tools` `Points in Polygon...`

![Points in Polygon](https://github.com/juanfrans-courses/mapping_arch_hum/blob/master/Fall_2016/Tutorials/Images/02_Data_Types_and_311/08_Points_in_Polygon.png)

* In the 'Points in Polygon' menu choose the following settings:
  * Input polygon vector layer: 'NYC_BlkGrp' - (this is the polygon layer we will join the points to)
  * Input point vector layer: '311_Data' - (this is the layer containing the points that will be joined)
  * Output count field name: '311_Count' - (this is a new field that will be created and will contain the count of points that were joined to each block group)
  * Output shapefile: '311_BlkGrp'
  * Check `Add result to canvas` so the new shapefile is added to the map.
* Once you have all your settings ready, click `OK` and let it run. Once it's done, click `Close`. You will see your new layer on the map.
* If you right-click on the new layer (311_BlkGrp) and choose 'Open Attribute Table' you will see that the last field is called '311_Count' and it contains the number of points joined to each block group. We will use this field to symbolize the block groups.
* To actually symbolize the layer, right-click on it and choose `Properties`, and in the Style tab change the 'Single Symbol' drop-down menu to 'Graduated'.
* Next, in the 'Column' drop-down menu select the '311_Count' field to symbolize and click on the `Classify` button to load the values.
* You will notice that qGIS automatically classifies the values into 5 categories. Also, if you look at the settings on the top right-hand side you will see that the software uses an 'Equal Interval' method for this classification. However, if you click `OK` and look at the resulting map you will notice that most block groups fall within the first group, the one that goes from 0 - 145.8 and that very few are fall in the other ones. In fact, it seems like there is one single block group with more than 400 complaints (located in Queens), which is skewing the whole classification method upwards. This is clearly an outlier and the classification method should not be based on this particular block group.
* Instead, go back to the properties and change the classification method to 'Natural Breaks (Jenks)' which deals better with datasets that are not normally distributed. You can find out more about this classification method [here](https://en.wikipedia.org/wiki/Jenks_natural_breaks_optimization).
* You can change your color ramp or the individual colors or strokes of each of the classes. You can also change the number of classes the data is divided into but note that normally, we can only really differentiate between 5 or 6 classes.
* Once you are done with the classification, click `OK` to apply it to the layer and see your results on the map.

![Classification Methods](https://github.com/juanfrans-courses/mapping_arch_hum/blob/master/Fall_2016/Tutorials/Images/02_Data_Types_and_311/09_Classification_Methods.png)

Lastly, we need to hide the census block groups that fall outside of the New York City borough boundaries. If you look closely at the census block group layer, you will see that there are some block groups that fall inside the Hudson River and that shouldn't be included in our map.

There are a couple of ways of doing this: one option would be to clip the block group layer using the borough layer, in order to get rid of the census block groups that fall outside the boroughs. However, this option would permanently modify the block group layer and, if at any point the borough boundaries don't align perfectly with the block groups (which is entirely possible), the geometry of those block groups would be changed too. The best option then is to hide the block groups that fall inside the water and conveniently enough there is a field in the block group attribute table that has a specific value for these features.
* First, open the attribute table of the census block group layer. You will notice that there is a field called 'ALAND' and another called 'AWATER'. 'ALAND' one has a unique identifier for each of the block groups that has some land area; 'AWATER' has an identifier for those block groups that have some water. There problem is that some block groups have both water and land. So we will only show those block groups where the 'ALAND' field does not equal 0, meaning that they have some land.
* To do this we will create a 'Feature subset'. Open the layer properties and go to the `General` tab. At the bottom of this tab you will see the 'Feature subset' panel. Go to the bottom of this panel and click on the `Query Builder` button. This query builder will work in a similar way as the 'Selection by attributes' query builder.
* In the 'Fields' panel you will see the 'ALAND' field. Double-click on this to make it appear in the bottom panel ('Provider specific filter expression').
* Now add '!= 0' to the expression. ('!=' means 'does not equal').
* Your expression should look something like this:

![Query Builder](https://github.com/juanfrans-courses/mapping_arch_hum/blob/master/Fall_2016/Tutorials/Images/02_Data_Types_and_311/10_Query_Builder.png)

* Click `OK` in the 'Query Builder' and then `OK` again in the 'Properties' panel. Your map should now only show the census block groups that have land.

Once you are finished with this go ahead and adjust colors, strokes and layer order. And finally, create a print composer, add a legend, title, explanation, source and a scale bar, and export your map as a PDF file. Your final map should look something like this:

![Final Map](https://github.com/juanfrans-courses/mapping_arch_hum/blob/master/Fall_2016/Tutorials/Images/02_Data_Types_and_311/11_Final_Map.png)

#### Deliverables
Two PDF 311 data maps. They should both be of something different than 'noise' complaints. One should be a qualitative map, showing the location of each complaint, and the other should be a quantitative map, showing the number of complaints per census block group in New York City. Your maps should include proper legends, scale bars, titles, explanations and sources. Choose colors, line weights and fonts wisely.
