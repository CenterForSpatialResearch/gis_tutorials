
## Downloading and Displaying Data from American FactFinder

# Using FactFinder to Find Census Data

Census data can be downloaded from the [American FactFinder](http://factfinder.census.gov/).

There are many ways to narrow down your search on the American FactFinder website. You can use `Community Facts` for popular tables for a city of interest. `Guided Search` filters by type of data, topics, geographies, and demographics. We will use the `Advanced Search` in this tutorial as it provides the most options for filtering your results.

Click on `Advanced Search` and `Show Me All`.

![t11-0.png](URL)

On the next page, the sidebar on the left includes options to search for data. These include `Topics` (age, income, year, dataset), `Geographies` (states, countries, places), Race and Ethnic Groups (race, ancestry, tribe), Industry Codes (NAICS industry), and `EEO Occupation Codes` (executives, analysts).

It is advised to use `Geographies` as an initial search because not all data is available at all scales of geography.

Click on `Geographies`. This will open a new dialog box titled `Select Geographies`.

![t11-1.png](URL)

You can browse the tabs at the top of the dialog box to browse by List, Name, Address, or Map. We will use the List tab. Make sure the `Select from` option is checked to `most requested geographic types`. For this tutorial we will select `Census Tract` from the `Select a geographic type` dropdown menu. We will select New York from the `Select a state` dropdown menu. We will select New York from the “Select a county” dropdown menu. Select `All Census Tracts within New York County, New York`. Next click `Add To Your Selections` at the bottom of the dialog box.

![t11-2.png](URL)

The geography will now be applied to your search and added to the `Your Selections` box on the top left side of the page. You can then close the `Select Geographies` dialog box.

The data available for the selected geography will be displayed as a list under `Search Results`. You can narrow your search from your selected geographies using the `Topics` tab on the left side of the page.

Click `Topics` at the left opening the `Select Topics` dialog box.

![t11-3.png](URL)

Once the dialog box opens, you can expand the topics to browse available datasets. For this tutorial we will expand the `Housing` topic, browse within `Financial Characteristic`, and select `Gross Rent`. Once you click on the topic it will be added to `Your Selections`. Then you may close the dialog box and return to the `Search Results`.

![t11-4.png](URL)

The list will now be updated to include the filters for both your selected `Geographies` and `Topics`.

![t11-5.png](URL)

To preview the content of each Table, File, or Document Title, you can click on the `About` icon on the right side of the list, with the `i` for information icon. An example of the data included will be previewed in a new window.

![t11-6.png](URL)

Once you find the dataset you wish to download, click on the dataset of interest. In this tutorial we will select `Gross Rent` also called table `B25063`. This opens a new window with a detailed preview of the dataset. Here you can download the data using the `Download` button on the `Actions` panel. Click on the `Download` button opening the `Download` dialog box.

![t9-7.png](URL)

In the `Download` dialog box choose the `Data and annotations in a single file` option and check the box `Include descriptive data element names` if you wish to include a description of each variable in the dataset.

![t11-8.png](URL)

If you select multiple datasets, you will have to download each dataset individually.

The dataset will be downloaded as a packaged zip file. You can now open your downloaded .csv files in Microsoft Excel.

TIGER shapefiles can be downloaded directly from the American Factfinder without having to navigate to a new webpage. In the preview page of your selected data, choose `Create Map`.

![t11-9.png](URL)

Click `Create Map`. Click on any piece of hyperlinked data in the table to create the map, in this case the first entry for the `Gross Rent Estimate` column. Once the map is created you can preview the map and legend. To download the associated TIGER shapefile, click “Download” from the “Actions” panel.

![t11-10.png](URL)

In the `Download` dialog box, select the option for “Shapefiles (.zip)” at the bottom of the window under `Spatial Data formats.` Click `OK` and `Download` in the next window. You may have to turn off pop-up blockers to download the data.

![t11-11.png](URL)

# Preparing FactFinder Data for Importing and Joining into ArcMap

Unzip the .zip file of the dataset you downloaded for Gross Rent and open the `.csv` file in Microsoft Excel. Choose the `ACS135YRB25063with_ann.csv`. We will need to modify this table so that it can properly join with the shapefile in ArcMap.

Once the file is open, ensure the following:

* Use only one header row. Rename these headers as meaningful to their associated data.
* Start data values in row 2.
* Ensure there are no special characters (periods, commas, ampersands, hyphens, etc.) in the headings.
* Delete any extra columns of data that you do not need in your dataset.

![t11-12.png](URL)

Once the modifications to the table are made, save the file in an Excel Workbook `.xlsx` format (Do not use Excel 97-2003). Close the Excel file after saving.

# Joining Excel Table to TIGER Shapefile in ArcMap

Open ArcMap and new blank map. Add the TIGER shapefile you unzipped to the map. You may have to `connect to folder` to locate the file. The shapefile will now be displayed on the map. Next add the Excel table to the map using the same technique. Please be aware that it will not correctly load unless you have closed the file in Excel first.

![t11-13.png](URL)

Note that in the attribute table for the TIGER file, the field name `GEO_ID` matches the first ID field in the Excel table you formatted. We will use these fields to join the data.

Right click on the layer name of the TIGER file and select `Joins & Relates` and then `Joins`. In the dialog box that appears, make sure the dropdown menu asking `What do you want to join to this layer?` is set to `Join attributes from a table.` Using the `GEO_ID` field for the tiger file, select the table to join to the layer and use the ID field you renamed in Excel containing the 20-digit Geo ID code. Ensure the `Keep all records` option is checked and select `OK`.

![t11-14.png](URL)

You can now open to attribute table of the TIGER file to view the joined dataset.

![t11-15.png](URL)

The join is only temporary unless you export the data as a new shapefile. Right click on the data and file name in the table of contents and navigate to `Data` > `Export Data`. When prompted to `add the exported data to the map as a layer` click yes and the new shapefile will now appear in the table of contents.

![t11-16.png](URL)

# Displaying and Visualizing Census Data

To graphically analyze the dataset you created and joined we can symbolize the data using the `Symbology` under the `Layer Properties`.

Right click on the newly added layer and select `Properties`. Under the tab named `Symbology`, select the “Quantities” on the left sidebar and choose `Graduated colors`. Choose the variable for the field `Gross_Rent`. You can choose a color ramp or create a custom ramp by right clicking on the color ramp. If you want to classify your data using specific breaks, click the `Classify` button to choose your selected method of breaks. You can also format labels to remove decimal points or change the significant figures of the displayed data. Select `Apply` and then `OK` and your shapefile will be symbolized using your specified parameters.

![t11-17.png](URL)

![t11-18.png](URL)

Source: American FactFinder, United States Census Bureau. U.S. Department of Commerce, 2000 http://factfinder.census.gov/