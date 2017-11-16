# Creating Basic Webmaps with Carto

## Getting Started 

The data used in this tutorial can be downloaded from the NYC Open Data website: [MapPLUTO-Manhattan](https://www1.nyc.gov/site/planning/data-maps/open-data/dwn-pluto-mappluto.page) and [NYC Wifi Hotspot Locations](https://data.cityofnewyork.us/City-Government/NYC-Wi-Fi-Hotspot-Locations-Map/7agf-bcsq). To download the files, click on the `Export` button above the map and select the desired file type. The former should be downloaded as a `shapefile` (vector) while the latter should be downloaded as a `CSV` (tabular data). 
![t27-0.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-0.png)

## Adding Data 
Click the `New Map` button on the top right of the page to get started. You will notice that the Building Footprints dataset was downloaded as a zip file. There is no need to unzip it, as it will be uploaded to Carto using that format. Alternatively, you can download vector files in the KML format, and these can be uploaded to Carto as well. Select the "Connect Dataset" tab to add data to your map. 
![t27-1.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-1.png)

Carto accepts different file formats from various places, including Dropbox, Google Drive, your computer or a website (Data file) and the ArcGIS web server. Add the building footprints zip file in the `Data file` tab and click `Connect Dataset` from the bottom right of the screen.
![t27-2.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-2.png)
![t27-3.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-3.png)

## Creating Maps
When the dataset has finished uploading (this may take a few minutes), you should see a list of maps you have made in Carto, including a map of the dataset that was just connected. Click on that to go into the map editing interface. It is important to note that the zip folder we added comes with two files: `mnmappluto`, which is the polygon shapefile of tax lot boundaries and `dcp_mappinglot`, which contains tax lot information. Take a second to familiarize yourself with the interface: clicking the `eye` icon beside layer names hide and show the layer, you can reorganize layers by dragging (the layer on top in the list = the layer on top in the map). Clicking the vertical ellipsis beside the map name `Mn Dcp Mappinglot 1` gives you the option to rename, download, edit metadata and duplicate. Clicking on the vertical ellipsis beside layer names gives you the option to rename, edit data, collapse and export (as a shapefile, KML, geoJSON or SVG. You can `add` data here as well, and add widgets to filter data, analyze and/or give more information. Zooming in Carto is controlled, and you can see the zoom factors/zoom in or out from the bottom left of the data frame (where you see the map). 
![t27-4.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-4.png)

## Editing Maps
Clicking on the `base map` layer takes you to a window where you can edit the style and/or change the basemap. 
![t27-5.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-5.png)

Clicking on any other layer name (layers with data) gives you expanded options for style, data and analysis. Importantly, toggling between the `map view` button (looks like a location marker) and `data view` button (looks like a table) allows you to switch between the mapping and data view. The data view shows the tabular data associated with the map, and allows for exploration of the fields in that data. Clicking the `edit feature` button to the left of these buttons allows you to create polygons.
![t27-6.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-6.png)

You can change the data type, order the cells and rename a field, and add, rename or delete a column by clicking on the vertical ellipsis beside any field name. To edit or rename cells or add or delete a column, click on the vertical ellipsis beside a cell. 
![t27-7.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-7.png)
![t27-8.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-8.png)

## Symbolizing by Value
There are many options for more advanced analysis in Carto, including creating and cleaning, analyzing and predicting, and transforming data, 
![t27-9.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-9.png)

For this tutorial, we will only be symbolizing data by value, which just means symbolizing the polygons (or points or lines if applicable) based on some predetermined attribute information. To do so, click on the layer name and go to the `STYLE` tab. Click on the box containing a colored line beside `COLOR` and change from `SOLID` to `BY VALUE`. Select/search for `yearbuilt` as the field to symbolize values based on. You can change the colors for the classification by selecting any of Carto`s pre-selected color sets, or you can click `Custom color set` at the bottom. Selecting the `flip` button beside a color set changes the order of colors. By default, Carto uses `Quantile` as the quantification method and classifies into `5 buckets`. Clicking on the ellipsis beside `Quantile` or `buckets` gives the option of changing the quantification method to Jenks, Equal Interval, Heads/Tails or Category.
![t27-10.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-10.png)
![t27-11.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-11.png)

The popup tab lets you add a field or fields to give more information when a feature on the map is clicked. 
![t27-12.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-12.png)

Click on the layer name and go to the `legend` tab  to create a legend. You`ll notice that there are `zero` values in the legend (and in the map), which should not be the case. To remove this, go to the `Data` tab and toggle from `value` to `SQL` at the bottom of the window. Type in `where yearbuilt > 0` at the end of the expression already there, and hit `APPLY`. This only shows values where the year built was above 0 on the map, and this logic can be used for creating other filtering statements. Changing the name of the layer also changes the title of the legend. Toggling from `Value` to `HTML` at the bottom of the window lets you add custom CSS to your legend (or styling) - this [guide](https://carto.com/learn/guides/styling/choropleth-map-for-statistical-data) is helpful for doing so. 
![t27-13.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-13.png)
![t27-14.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-14.png)
![t27-15.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-15.png)

## Working with tabular data (CSVs)

The process for working with tabular data is very similar to that for vector data, but for a few differences. Add the NYC wifi hotspot locations CSV to the map by `connecting dataset`. The dataset contains latitude and longitude values, but no shape values so it imports as points. In the `STYLE` menu, the options for symbology include points (with color by value), squares, hex bins, animated (you can control the time/animation) and pixel (heatmap) among others. The same rules apply for changing colors, quantification/classification type, and number of bins/resolution.
![t27-16.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-16.png)
![t27-17.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-17.png)
![t27-18.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-18.png)

## Finishing Up
*Currently, Carto`s options to add `Elements` to a map, i.e. titles and text (for explanations and sources) has been disabled - it will be restored soon.*

When you are finished with your map, you can export it as an `image` and/or `publish` it to the web. To export as a JPG or PNG, click the vertical ellipsis beside the file name and select `Export image`. Within the map window, you will be able to select a portion of the map to export at your zoom level. 
![t27-19.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-19.png)
![t27-20.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-20.png)

To publish to the web, select the publish button at the bottom left of the screen. Here, you can select whether it is published to the public or private (only accessible via link).
![t27-21.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_27/t27-21.png)

 
