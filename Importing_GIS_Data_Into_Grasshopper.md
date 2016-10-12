## Importing GIS Data into Grasshopper

This tutorial will cover some basic techniques for importing GIS data into Rhino—using the Grasshopper plugin—in order to create a 3D site model with basic building masses. This method generates NURBS geometry in Rhino, allowing you to use features like Make2D to export vector graphics.

This tutorial uses the TT Toolbox plugin for Grasshopper to read Excel spreadsheets.

TT Toolbox can be downloaded [here](http://www.food4rhino.com/project/tttoolbox?ufh).

# Preparing Data in ArcGIS

This exercise uses a building footprint shapefile and visualizes the height of the buildings by extruding with height data in the shape file’s attributes.

For this exercise, we will be using Building Footprint data for NYC from the BYTES of the BIG APPLE PLUTO files shapefile found here: 

Open ArcMap. (You will find it in your start menu under `Programs` > `ArcGIS` > `ArcMap`)

Add the Data to the map. Once you’ve added your data, it will appear in the preview window.

![t12-0.png](URL)

Using the selection tools, highlight the area you are looking to visualize.

![t12-1.png](URL)

Export the selected data as a new shapefile. Right click on the data layer and `Data` > `Export Data`

![t12-2.png](URL)

Make sure that the pull-down menu at the top of the export dialog box is set to Selected records, pick a location to save the file, and set the file type to Shapefile.

# Preparing Attribute Data in Excel

Open Microsoft Excel.

Open the exported shapefile database (DBF file extension). Navigate to the folder where you exported your shapefile of selected building footprints, and open the file with the `.dbf` extension. If you do not see this file in the Excel Open menu, make sure the pull down menu for visible filetypes is set to `All Files`.

Save As this file as an Excel Workbook (`.xlsx` extension).

# Importing Spatial Data into Grasshopper

![t12-3.png](URL)

Open Rhino 5. Make sure your units are set to Feet.

Open up Grasshopper.

![t12-4.png](URL)

Load Building Footprints with the `Import SHP` component. Create a `File Path` component, an `Import SHP` component, and a `Curve` component. Right click on the `File Path` component and use the `Set One File Path` command to link to the exported shapefile (.shp file extension).

Note: SHP component may only open shapefiles in Rhinoceros 5 (not the 64-Bit version).

![t12-5.png](URL)

Convert `Curves` to `Boundary Surfaces`. Connect the `Curve` component to a `Boundary Surface` component. This ensures that footprints with nested curves (courtyards) are only counted as a single item.

# Import Attribute Data into Grasshopper

![t12-6.png](URL)

Connect to Excel spreadsheet. Locate the attributes spreadsheet with a `File Path` component. Right-click the `File Path` component, choose Set One `File Path`, and choose the Excel workbook you saved earlier.

Import data from Excel Spreadsheet. Connect the `File Path` component to a `Read Excel Sheet` component (from TT Toolbox). Connect the `File Path` component to the [Fp] input, and create a `Boolean Toggle` component (under the first component tab, `Params` > `Input`) and connect it to the R input. Set the `Boolean Toggle` to True to get the `Read Excel Sheet` component to import the attributes file.

![t12-7.png](URL)

Copy the Excel data into a `Data` component. Create a `Data` component and connect the Columns (C) output of the `Read Excel Sheet` component to the `Data` component. Right-click on the `Data` component and select `Internalize` data. While this step is not necessary, it will embed the data into the Grasshopper file and speed up the calculation process.

![t12-8.png](URL)

Now it is time to extract height data. Create a `Tree Branch Index` component and connect the `Data` component to the `Data Tree` (T) input. Then, create a `Number Slider` of integers, and connect it to the `Tree Branch Index` component’s `Branch Index` (i) input. Create a `Split List` component, and connect the output of the `Tree Branch Index` component to the `List` (L) input. Create a `Panel` or `Number Slider` component with the value `1` and connect it to the `Splitting Index` (i) input. Finally, create two `Panel` components and connect them to the (A) and (B) outputs of the `Split List` component.

You should now see the field name in the panel connected to (A) and the values in the panel connected to (B). Changing the slider connected to the `Branch Index` will change between all of the fields (the columns from the Excel file), and `45` should be the field NumFloors" in this example.

# Extruding Building Footprints

![t12-9.png](URL)

Calculate extrusion height from number of floors. Create a Multiplication component and connect the (B) output from the Split List component (the values for number of floors) to the (A) input of the Multiplication component. Create a Number Slider and connect it to the (B) input of the Multiplication component. This will be your typical floor-to-floor height, which is around 12 to 14 feet for NYC. Create a Unit Z Vector component and connect the Multiplication output (R) to the vector’s input (F) to make sure we are extruding vertically.

![t12-10.png](URL)

Extrude building footprints. Create an `Extrude` component, and connect the surfaces of building footprints from the `Boundary Surface` component’s (S) output to the `Extrude` components Base (B) input. Then connect the `Unit Z` Vector’s output (V) to the `Extrude` component’s `Direction` (D) input.

![t12-11.png](URL)

Bake geometry into Rhino. Right click the `Extrude` component and select Bake.