# Importing GIS Data into Grasshopper

This tutorial will cover some basic techniques for importing GIS data into Rhino—using the Grasshopper plugin—in order to create a 3D site model with basic building masses. This method generates NURBS geometry in Rhino, allowing you to use features like Make2D to export vector graphics.

This tutorial uses the TT Toolbox plugin for Grasshopper to read Excel spreadsheets.

TT Toolbox can be downloaded [here](http://www.food4rhino.com/project/tttoolbox?ufh).

## Preparing Data in ArcGIS

This exercise uses a building footprint shapefile and visualizes the height of the buildings by extruding with height data in the shape file’s attributes.

For this exercise, we will be using the [Building Footprint](https://data.cityofnewyork.us/Housing-Development/Building-Footprints/nqwf-w8eh) dataset for NYC Open Data.

Open ArcMap. (You will find it in your start menu under `Programs` > `ArcGIS` > `ArcMap`)

![t12-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-0.png)

Add the Data to the map. Once you’ve added your data, it will appear in the preview window.

![t12-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-1.png)

Using the selection tools, highlight the area you are looking to visualize.

![t12-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-2.png)

Export the selected data as a new shapefile. Right click on the data layer and `Data` > `Export Data`

![t12-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-3.png)

Make sure that the pull-down menu at the top of the export dialog box is set to Selected records, pick a location to save the file, and set the file type to Shapefile.

## Preparing Attribute Data in Excel

Open Microsoft Excel.

![t12-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-4.png)

Open the exported shapefile database (DBF file extension). Navigate to the folder where you exported your shapefile of selected building footprints, and open the file with the `.dbf` extension. If you do not see this file in the Excel Open menu, make sure the pull down menu for visible filetypes is set to `All Files`.

Notice that the 7th column (assuming the first column is column 0) contains the data for the roof height or `HEIGHT_ROO`.

Save As this file as an Excel Workbook (`.xlsx` extension).

## Importing Spatial Data into Grasshopper

![t12-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-5.png)

Open Rhino 5. Make sure your units are set to Feet.

Open up Grasshopper.

![t12-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-6.png)

Load Building Footprints with the `Import SHP` component. Create a `File Path` component, an `Import SHP` component, and a `Curve` component. Right click on the `File Path` component and use the `Set One File Path` command to link to the exported shapefile (`.shp` file extension, or AutoCAD Shape Source file).

Note: the `.shp` component effectively converts from your Coordinate System in ArcMap to the Euclidean coordinates in Rhino. You can add as many shapefiles into Rhino as you like and they will align properly as long as they were created in the same coordinate system and projection in ArcMap.

![t12-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-7.png)

Convert `Curves` to `Boundary Surfaces`. Connect the `Curve` component to a `Boundary Surface` component. This ensures that footprints with nested curves (courtyards) are only counted as a single item.

## Import Attribute Data into Grasshopper

![t12-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-8.png)

Connect to Excel spreadsheet. Locate the attributes spreadsheet with a `File Path` component. Right-click the `File Path` component, choose Set One `File Path`, and choose the Excel workbook you saved earlier.

Import data from Excel Spreadsheet. Connect the `File Path` component to a `Read Excel Sheet` component (from TT Toolbox). Connect the `File Path` component to the [Fp] input, and create a `Boolean Toggle` component (under the first component tab, `Params` > `Input`) and connect it to the R input. Set the `Boolean Toggle` to True to get the `Read Excel Sheet` component to import the attributes file.

![t12-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-9.png)

Copy the Excel data into a `Data` component. Create a `Data` component and connect the Columns (C) output of the `Read Excel Sheet` component to the `Data` component. Right-click on the `Data` component and select `Internalize` data. While this step is not necessary, it will embed the data into the Grasshopper file and speed up the calculation process.

![t12-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-10.png)

Now it is time to extract height data. Create a `Tree Branch Index` component and connect the `Data` component to the `Data Tree` (T) input. Then, create a `Number Slider` of integers, and connect it to the `Tree Branch Index` component’s `Branch Index` (i) input. Create a `Split List` component, and connect the output of the `Tree Branch Index` component to the `List` (L) input. Create a `Panel` or `Number Slider` component with the value `1` and connect it to the `Splitting Index` (i) input. Finally, create two `Panel` components and connect them to the `A` and `B` outputs of the `Split List` component.

You should now see the field name in the panel connected to `A` and the values in the panel connected to (B). Changing the slider connected to the `Branch Index` will change between all of the fields (this corresponds to the column number from the Excel file), and `7` should be the field `HEIGHT_ROO` in this example, which is the building height from it's ground elevation to the roof.

## Extruding Building Footprints

![t12-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-11.png)

Create a `Unit Z` Vector component and connect the `B` output of the `Split List` to the factor `F` input of the `Unit Z` Vector.

Create an `Extrude` component, and connect the surfaces of building footprints from the `Boundary Surface` component’s `S` output to the `Extrude` components Base `B` input. Then connect the `Unit Z` Vector’s output (V) to the `Extrude` component’s `Direction` (D) input.

![t12-12.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-12.png)

Bake geometry into Rhino. Right click the `Extrude` component and select Bake

![t12-13.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_12/t12-13.png)

Your GIS data will now be baked into Rhino.
