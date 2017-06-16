## Analyzing Data

Through this exercise you will learn key tools of analysis using ArcMap. After completing these exercises you should be able to…

* Use proximity based measures
* Understand the principles and applications of boolean operations
* Conduct spatial joins
* Explain and perform proportional split population estimates
* Create a basic density map (and understand the potential pitfalls of this type of visualization)
* Perform basic raster math operations
* Develop a raster based decision mapping methodology to answer a specific question
* Adapt a raster dataset to your own research needs through raster re-classification

### Analyzing Data 01: Libraries, Education, and Language

#### Premise
We are interested in looking at libraries in the Bronx as a public resource. We will use proximity based measures to the zones of impact (and potential impact) of libraries on Bronx residents from a number of different perspectives. First we want to evaluate which library branches are located within areas that have a high number of Spanish speaking residents. Then we will evaluate which libraries serve the greatest number of school children.  

#### Research questions:
* Where are Bronx Library branches?
* Which Library branch locations are within areas with a high number of Spanish speaking residents?
* How many public schools are located within 1/4 mile of a library?
* Which five Libraries serve the most students?
* What is the nearest library to each school?
* How many people do these libraries serve?

#### The Strategy
To evaluate the confluence of Spanish speakers and branch libraries we will first select using an expression and then select by area to identify which libraries fall in census tracts with a high percentage of Spanish speakers.

Then to evaluate which libraries serve the greatest number of school children we will first create a buffer around each library location of ½ mile (which we will be able to export as its own layer to display on our map). We will then use a spatial join in order to count the number of schools within ½ mile of a library and to determine the number of students enrolled in those schools.

#### Before you begin
Download the data needed for this tutorial from the X drive:
\gis\GIS_Classes\GIS_Workshops\GIS_UD_AnalyzingData_Tutorial

#### Let’s Begin

**Launch** ArcMap.

* Choose a **Blank Map** from **My Templates**
* Navigate to `Customize`>`Extensions...` and make sure all are turned on

Right-click `Layers`, choose `Add Data...`, and navigate to the folder where you have saved the data and add the following three Layers:
* Bronx_Tracts_2014.shp
* Bronx_Schools.shp
* Bronx_Libraries.shp

![add](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/01_Layers.png)

In the layers panel, right-click each data layer and choose `Open Attribute Table` to inspect its contents.

The field names for `Bronx_Tracts_2014` are:
* `STATEFP`: the State FIPS code
* `COUNTYFP`: the county FIPS code
* `TRACTCE`: the FIPS code for the census tract
* `GEOID`: the unique FIPS code that combines the state, county, and tract code for each tract.
* `NAMESLAD`: the name of the census tract
* `ALAND`: the area of the census tract that is land
* `AWATER`: the area of the census tract that is water
* `INTPTLAT`: the latitude coordinate of the locator of the census tract
* `INTPTLON`: the longitude coordinate of the locators of the census tract
* `Pop2014`: the population of the census tract in 2014 according to the [American Community Survey 2014 5 Year Estimates](http://factfinder.census.gov/faces/tableservices/jsf/pages/productview.xhtml?pid=ACS_14_5YR_B01003&prodType=table)
* `PopOver5`: Population over 5 Years old
* `Pct_OnlyEn`: the percent of the population over 5 years old within the census tract that speaks only English
* `Pct_Other`: the percent of the population over 5 years old within the census tract that speaks another language in addition to (or instead of) English
* `Pct_Spanis`: the percent of the percent of the population over 5 years old within the census tract that speaks Spanish

The field names for `Bronx_Libraries` are:
* `facname`: the name of the facility
* `borough`: the borough of the library – in this case they are all in the Bronx
* `ft_decode`: the type of library it is, Branch or Central
* `facaddress`: the address of the library
* `zipcode`: the zipcode of the library

The field names for `Bronx_Schools` are:
* `BORO`: a code for the name of the borough the school is within
* `BORONUM`: a numeric code for the borough the school is within
* `SCHOOLNAME`: the name of the school
* `SCH_TYPE`: the type of school, Elementary, K-8 etc
* `ADDRESS`: the school’s address
* `ZIP`: the school’s zipcode
* `GRADES`: the grades within the school
* `Enrollment`: the number of students enrolled in the school

**Save** your map project as `AnalyzingData.mxd`

#### Finding libraries near concentrations of Spanish speakers

Now, we want to determine which libraries are located within census tracts where more than 65% of the population speaks Spanish. We are interested in determining which libraries might be well suited to receive additional resources to go towards multilingual programs.

* **Navigate** to menu item `Selection` > `Select by Attributes`. Make sure that `Bronx_Tracts_2014` is the active selection layer and the selection method is set to `Create a new selection`. **Double-click** `Pct_Spanis`, **click** `>`, and **type** `65`. Your expression should look like this: `"Pct_Spanis" > 65`. Click `OK`. In the bottom-left corner of the ArcMap window, you should see that 56 features were selected.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/02_SelectionExpression.png)

* **Right-click** on the `Bronx_Tracts_2014` layer and choose `Selection` > `Create Layer From Selected features`. A new layer will appear on top. Clear selection by navigating to menu item `Selection` > `Clear Selected Features`. **Right-click** on the new layer and choose `Properties...` In the `General` tab, rename the layer to `Bronx_Tracts_Spanish`. In the `Symbology` tab, choose a fill color that differs from the `Bronx_Tracts_2014` layer. Arrange the layer order so that schools and libraries are the top two layers.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/03_NewLayer.png)

* Now we will determine which libraries lie within these census tracts by using the select by location tool. **Navigate** to menu item `Selection` > `Select by Location...` Set the target layer to `Bronx_Libraries` and the source layer to `Bronx_Tracts_Spanish`. Set the selection method for target layer features to `are within the source layer feature` and click `OK`. Your selections should look like this:

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/04_SelectByLocation.png)

* Open the attribute table of the `Bronx_Libraries` layer in order to note which libraries were selected. Four libraries were selected, what are their names?

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/05_Attribute.png)

This analysis give us a very rough sense of which libraries might already serve a large number of Spanish speakers however we have only selected libraries which are located exactly within census tracts with a large proportion of Spanish speakers. What is there is a library in an adjacent census tract? Our analysis will not have picked up on this.


**Save** your map project.

#### Schools and Libraries
Now we will depart from questions about language and instead ask a series of questions about the relationship between schools and libraries in the Bronx. Specifically we will ask:
* How many schools are within 1/4 mile of Bronx libraries?
* How many students are enrolled in schools that are within ¼ mile of a Bronx library?
* What is the nearest library to each school?

To answer the first question, we will create a 1/4 mile buffer around the libraries.

We will be creating a number of new layers during this portion of the exercise so in order to save all of these layers produced in the process of our analysis lets first create a new folder within the project folder and name it `MyShapes`. Save all new layers created during this exercise in this folder.

##### Creating Buffers
* Navigate to menu item `Selection` > `Clear Selected Features` to deselect the libraries.
* Navigate to menu item `Geoprocessing` > `Buffer`.

![buffer](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/06_Buffer.png)

  * Set Input Features to `Bronx_Libraries` – this sets which layer the buffers are drawn around.
  * Set the Output Feature Class to `BX_Library_QuarterMiBuffer.shp` within your 'MyShapes' folder.
  * Set the buffer distance to 0.25 and set the unit to Miles.
  * Click `OK`. Your map should look something like the following:

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/07_Buffer_map.png)

* Next we will use the select by location tool to determine which schools fall within ¼ mile of a library. Navigate to menu item `Selection`>`Select By Location`
  * Set Target Layer to `Bronx_Schools` and Source Layer to `BX_Library_QuarterMiBuffer`. Keep the selection method for target layer features to `interect the source layer feature`.
  * Click `OK`.

  * Open the attribute table of `Bronx_Schools` and notice that 92 schools were selected. Thus there are 92 schools in the Bronx that are within ¼ mile of a library.

*  Now we want to answer our second question:  Which five libraries serve the greatest number of school children? To answer this, we will perform a *spatial join*. A spatial join is a new tool for us which allows us to summarize the attributes from one layer within the attribute table of another based on the spatial relationship between them.

  * Deselect the schools by navigating to `Selection` > `Clear Selected Features`.  
  **Right-click** on `BX_Library_QuarterMiBuffer` and choose `Joins and Relates` > `Join...`.
  * Choose `Join data from another layer based on a spatial location` from the drop-down menu.
  * Choose `Bronx_Schools` as the layer to join to this layer.  


* Because there might be multiple features in the join layer within one of the target layer features we need to tell ArcMap how we would like to summarize the attributes from the Bronx Schools layer when they are joined to the buffer around the libraries. We can tell ArcMap to take the values of the attribute fields for the first school it finds or to compute a summary (either Mean, Min, Max, Sum, or Median) of the values of all features in the schools layer which lie within the target features.

    * We want to know the total number of students enrolled in the schools which are within our ¼ mile buffers and thus we will **select** `Sum`.  
    * Save the output shapefile within 'MyShapes' as `Library_QuartMiBuffer_SchoolsJoin`.  
    * Click `OK`.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/08_SpatialJoin.png)


  * Note that `Library_QuarterMiBuffer_SchoolsJoin` has now been added to your map as a layer.

  * **Open** the attribute table for this layer. Notice the new field `SUM_Enroll` that has been added on. This field contains the sum of the enrollments for all of the schools within the buffer.

  * Which five libraries serve the greatest number of enrolled school children. Sort the attribute table by SUMEnrollment and identify the top five libraries.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/09_SumEnroll.png)

**Save** your map project

##### Using a Distance Matrix

*  Now we will move on to answer our third question: which is the nearest library to each public school? To answer this question we will again introduce a new tool of analysis  - `Near` tool. This tool takes two point layers and computes the linear distance between each feature in both layers.  

  *  Navigate to `Geoprocessing` > `ArcToolbox` > `Analysis Tools` > `Proximity` > `Near`  

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/10_Near.png)

  * Set Input Features to `Bronx_Schools`. The input features is the layer that the distance of the near features will be measured in relation to.
  * Set Near Features to `Bronx_Libraries`.
  * Click `OK`.
  * Open Attribute Table of the `Bronx_Schools` layer. You will notice that we have generated two new fields: `NEAR_FID` and `NEAR_DIST`. `NEAR_FID` is the identifier of the nearest library matched with each school, and `NEAR_FID` is the distance between them in feet. We will use this identifier to add  the name of the nearest library for each school the table.  

  ![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/11_Near.png)  

  * **Right-click** `Bronx_Schools` and choose `Joins and Relates` > `Join...`.
  * Choose `Join Attributes from a Table` from the drop-down menu. Set the field in this layer that the join will be based on to `NEAR_FID`. Set `Bronx_Libraries` as the table to join to this layer. Choose the field in the table that the join will be based on to `FID`. You can keep only the matching records.
  * Click `OK` and open the attribute table of the `Bronx_Schools` layer. Notice that we now have names of the nearest libraries added to the table.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/12_TableJoin.png)

##### Making Estimates
We now have gathered information about how many schools are within ¼ mile of each library, as well as the total number of children enrolled in those schools and we have also computed the nearest library to each school. Now we would like to determine more generally how many people live near libraries in the Bronx – i.e. how many people do Bronx libraries serve?

In order to answer this question we will need to estimate the total population near libraries in the Bronx. We will first use a coarse method of estimation and then we will refine our estimate using a more advanced technique.

For our first approximation we will ask: how many people live in the census tracts that intersect a ¼ mile buffer around our libraries?

* We will use the select by location tool to select all of the census tracts that intersect one of our ¼ mile buffers around the libraries.

* Navigate to menu item `Selection`>`Select by location`.
* Set the Target Layer to `Bronx_Tracts_2014`. Set the Source Layer to `BX_Library_QuarterMiBuffer`. Leave the selection method to `intersect  the source layer feature`.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/13_Select.png)

* Click `Apply`.
* Your selections should look something like this:
![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/14_Selection.png)

* We can already tell that this will be a very coarse way to estimate the population served by each of the Bronx libraries because some census tracts which intersect our buffers are very large and portions of the tract are very far away from any library.

* Despite this we now want to add up the total population within these selected census tracts.  To determine the total population of all of the census tracts that intersect a ¼ mile buffer of a Bronx library. To do this we will use the `Summary Statistics` tool. Navigate to  `Geoprocessing` > `ArcToolbox` > `Analysis Tools` > `Statistics` > `Summary Statistics`. Set the Input Table to `Bronx_Tracts_2014`. Save the Output Table to `Bx_Tracts_Stats`. Set the Statistics Field to `Pop2014` and `Statistics Type` to `SUM`. Click `OK`.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/15_Summary.png)

* A new table has been generated. We see that the total population of all of the census tracts that intersect a ¼ mile buffer around a Bronx library is 988,651. Make a note of this total we will compare it to the result we get in the next portion of the exercise.

Now we will refine our estimate of the population near libraries. We will estimate the population that lives precisely within our ¼ mile buffers using using a method called *proportional split estimation*. A proportional split is a way to estimate the proportion of a quantitative attribute that falls within a portion of a polygon’s area. A proportional split is calculated in a few fairly simple steps.

1. We calculate the area of each polygon unit
2. Clip the polygons to the boundary of the study area (in our case the ¼ mile buffers)
3. Calculate the area of the polygons after clipping them to the study area
4. Divide the area of the polygons within the study area by their original area to determine the proportion of the original area that falls within the study area
5. Multiply the attributes (for us, population in 2014) we wish to estimate by the proportion in order to estimate the proportion of the attribute that falls within the study area.
Note: that proportional split estimation assumes that the attribute you are estimating is evenly distributed through out the polygon. In reality the population within each census tract is not evenly distributed nevertheless thus this is an estimate.


**Calculating the area of the census tracts**
* Open the attribute table for the Bronx census tracts layer and click the “Table Options” icon and choose `Add Field`.
* Name the filed `Area`, of type `Double`.
* Click `OK`.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/16_Area.png)  

* Right-Click on the `Area` field and choose `Calculate Geometry`. Ignore warnings. Set the Property to `Area` and click `OK`.

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/17_CalculateGeometry.png)


* Scroll to the right in the attribute table for the Bronx census tracts and see the new field that you have added.
* Note: census tracts extend into the water so the area we are calculating here includes both land area and area of the tract that might be in the water. This introduces some error into our proportional split estimation. One way to be even more precise in our estimate is to clip the census tract polygons by the shoreline prior to embarking on this analysis.  

**Clipping the census tracts to the ¼ mile buffers**  

* Next we will use the `clip` tool to clip the Bronx census tracts with the ¼ mile buffers around the Bronx libraries.
* Navigate to `Geoprocessing`>`Clip`.
* Set the Input Features to `Bronx_Tracts_2014`.
* Set the Clip Features to `BX_Library_QuarterMiBuffer`.
* Save the Output Feature Class within the 'MyShapes' folder as `BXTracts_LibraryQuartMiClip.shp`.
* Click `OK`.
* A new layer containing the census tracts clipped to the ¼ mile buffers around the libraries was added to your map.
* Toggle the visibility of all of the layers on your map off except for `BXTracts_LibraryQuartMiClip`.
* Use the Identify tool to click on some of the individual clipped census tract polygons to familiarize yourself with this new layer.  

 ![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/18_Clip.png)

**Calculating the area of the clipped census tracts**  

* Now we will calculate the area of these new polygons.
* Open the attribute table for the clipped Bronx census tracts layer: `BXTracts_LibraryQuartMiClip`.
* Create a new field again to calculate the new area of each polygon.
* Name the field `AreaClip`, of type `Double`. Click `OK`.
* Notice the new field that has been added to the far right of the attribute table called `AreaClip`. Right-Click on `AreaClip` and choose `Calculate Geometry`. Set the Property to `Area` and click `OK`.  

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/19_AreaClip.png)

**Dividing the area of the clipped census tracts by their original area**  

* With attribute table still open, add a new field.
* Name the field `Proportion`, of type `Double`.
* Right-Click on the new field `Proportion` and choose `Field Calculator...`. Ignore warnings.
* Double-click `AreaClip`, Click `/` sign, and double-click `Area`. Your calculation should look like this: `[AreaClip]/[Area]` -- i.e. the proportion of the original area that remained after the clip.
* Click `OK`  

![location](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/Images/Tutorial_24/20_FieldCalculator.png)

**Multiplying the population by the proportion**

* Now we will calculate one final field where we’ll multiply the attributes in order to estimate the proportion of the attribute that falls within the study area.
* Add new field and name it `Pop2014_cl` of type `Double`.
* Right-Click on the new field `Pop2014_cl` and choose `Field Calculator...`. Ignore warnings.
* Double-click `Proportion`, click `*` sign, and double-click `Pop2014`. Your calculation should look like this: `[Proportion] * [Pop2014]`.
* Click `OK`
* Close the attribute table.

Now we will compare the total estimated population within the buffers to the original rough population estimate we made at the beginning of this exercise using the select by location tool.

* Navigate to  `Geoprocessing` > `ArcToolbox` > `Analysis Tools` > `Statistics` > `Summary Statistics`. Set the Input Table to `BXTracts_LibraryQuartMiClip`. Save the Output Table to `Bx_Tracts_cl_Stats`. Set the Statistics Field to `Pop2014_cl` and `Statistics Type` to `SUM`. Click `OK`.
* Open the new table: 376,409
* Repeat for the population field for the entire census tract Pop2014 and note the difference: 983,821

______________________________________________________________________________________________________________

Original version of this tutorial is written by Dare Brawley, for *Mapping for the Urban Humanities*, a intensive workshop for Columbia University faculty taught in Summer 2016 by the [Center for Spatial Research](http://c4sr.columbia.edu). More information about the course is available [here](http://c4sr.columbia.edu/courses/mapping-urban-humanities-summer-bootcamp). ArcMap conversion by Grga Basic, Center for Spatial Research.
