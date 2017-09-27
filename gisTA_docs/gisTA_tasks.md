## Tasks for the GIS TA

### Overview
Your responsibilities includes the management of data on the X drive, including acquisition of new data and the maintenance and documentation of existing data, as well as providing assistance to GSAPP students and faculty in finding and using GIS data and software.

The position requires a strong familiarity with the GIS data and GIS software. You are not expected to be an expert, but you should be able to assist with the most common tasks performed in GIS at GSAPP as well as be able to find and provide references for tasks and functions you are less-familiar with.

The workload for the position varies throughout the semester, and you will have to find a balance between the short-term and long-term tasks. Typically, the beginning of the semester has a heavier workload, including workshops and studio data requests from professors. Following midterms, most students have completed their analytical work, so the need for GIS help diminishes.

### Data to download and update (on to the X drive)
* [Bytes of the Big Apple](https://www1.nyc.gov/site/planning/data-maps/open-data.page)
  * Download all datasets to upload onto the X Drive
  * [PLUTO Data](https://www1.nyc.gov/site/planning/data-maps/open-data/dwn-pluto-mappluto.page) (download all PLUTO and MapPLUTO data yearly)
* Other datasets
	* https://data.cityofnewyork.us/widgets/dpc8-z3jc
	* http://www1.nyc.gov/site/doitt/initiatives/3d-building.page
	* https://data.cityofnewyork.us/Transportation/NYC-Planimetrics/wt4d-p43d
* Specific data based on projects and accompanying studios.
* Organize data by geography on the X drive.
* Add data to master Excel File on the X drive.

### Specific GIS workshops for studios
* Pending request from faculty for specific studio workshops
* Request desired focus or intention with spatial data or mappings in the studio

### Write and update GIS tutorials
* Create text documents (.md) of tutorials as a text document
* Create a folder for images and key images within master folder
* Include description before tutorials explaining what the tutorial will accomplish.
* Include key image and description to be used on C4SR website
* Push to Github [tutorial repository](https://github.com/CenterForSpatialResearch/gis_tutorials) and create entry in C4SR site

### GIS Workshops (Beginning of Each Semester)
* Directly email specific faculty members announcing GIS Workshops (MArch, UD, HP)
* Reserve and book room in 202 Fayerweather for GIS Workshops (email Stephanie Cha-Ramos sc3600@columbia.edu)
* Create workshop poster to use in emails, social media, and post in designated boards in Avery Hall and Fayerweather
* Email Danielle Smoller (ds89@columbia.edu) to send out email to all students and faculty the first week of classes
* Download data and prepare presentation in computer lab prior to workshops

#### Email Template:
```
Hi [Dean],

The Center for Spatial Research will provide both GIS workshops and data services for the [fall or spring] semester. In addition, we want to know if architecture, historic preservation, or urban design professors need specific data or assistance with GIS.

Could you please send out the following email with the included attachment? The email should be sent via the listserv to include all AAD, ARCH, HP, and UD students.

Thank you!

Best,
[GIS TA]

---------------------------------------------------------------------------------------------

GIS WORKSHOPS, DATA, & TUTORIALS

The Center for Spatial Research will be providing workshops in the beginning of the spring semester to give students an introduction to GIS and show them how to use some of the geographic data on the server.

We will be offering workshops for Architecture, Historic Preservation, and Urban Design students at the beginning of the semester. These workshops provide a basic familiarity in working with GIS data, including mapping data in the ArcGIS software suite and exporting data for use in the CAD and 3D software packages installed on all GSAPP workstations. All workshops are located in Fayerweather 202.

GIS FOR DESIGNERS: 2D BASICS
[day(s), date(s), and time(s)]

Some topics will include how to find and open data from the data archive, locate data not in the archive, visualize data in GIS, export data to CAD and Illustrator.

GIS FOR DESIGNERS: 3D TECHNIQUES
[day(s), date(s), and time(s)]

Some topics will include creating surfaces from point data, automatically extruding building footprints, creating elevation data and understanding elevation data types, and exporting any 3D data into other modeling software (such as Rhino, Illustrator, and 3dsMax).

GIS DATA

Please let us know if there is a specific area in which your studio may need base data - as the Center for Spatial Research collects data from all over the world, Hong Kong to Johannesburg, so we may have data your studio needs for the semester.

GIS TUTORIALS

The GIS Tutorials have been updated this semester and can be found on the Center's website. We have added several advanced tutorials that integrate Grasshopper plugins, Google Earth, and Google Maps to help visualize spatial data. http://c4sr.columbia.edu/tutorials

Questions can be directed to [GIS TA], ([your email]), the GIS student coordinator.
```

#### GIS Workshop Outline

*Copy Folder to D Drive*

**Session 1:**
1. Powerpoint presentation on GIS

        What is GIS/what can you do with it?
        What is it used for? Maybe show slides of cool maps that are relevant to
        architecture
        Resources at GSAPP and Columbia for GIS
        Working with GIS:
          Types of files - raster vs vector
          What is a shapefile? What is a geodatabase?
          Projections - what it is and why it's so important
            show slides of NYC projected in different projections +
            compare to regular one

2. Overview of the X drive

        What it is + what type of data is on there
        Demo of how to get to the X drive and where to find data on there
        Where else can you find data online?
          Show American Community Survey, Bytes of the Big Apple, NYC Open Data

3. Programs

        Demo of using ArcCatalog
          Interface + how to use it
          Copy files for the tutorial from the X drive
        Demo of using ArcMap
          Interface
            Also show how to get to ArcCatalog from here
            ArcToolbox
            Search
          Data vs Layout window
            go to properties for layout window to show how you can change page
            sizes + for data frame to show coordinate system

----------WORKSHOP----------------------------

**Session 1: Making a 2D model of Morningside Heights**

      a. Exercise 1 - creating and exporting a basic site plan
          Open ArcMap - set Default Geodatabase
          Add Data - connect to local folder - data = borough boundaries,
          water, green space
            Brief note on projections and how the first file you put in sets
            the coordinate system for the data frame
            project parks from WGS84 to NAD83
            Mention that NAD83 is NYC projection and WGS84 is general GPS one
          More on interface:
            selection, information, measurement tools. also selecting
            interactively and by polygon, etc (from toolbar), remove from
            selection
            Moving layers
            Right-clicking on layer to get layer properties (in source here,
            you can see the projection i.e. the map's units)
          Attribute table:
            open the borough boundaries attribute table and go super briefly
            into what it is, what data it contains.
            select interactively from attribute table and from the data frame

          Add Data - building footprints
          ***note how the buildings load slowly - file is huge***
          Symbology:
            Just change colors, etc of the map to make it look decent
            Now open the attribute table for building footprints and explore
            what you have on there
              Metadata: Go to the nyc open data link and look at the metadata to
              figure out what all the fields mean
            Go back to layer properties and the symbology tab -
              [I show the below and tell people to symbolize how they want]
              Symbolize by category: any qualitative data (building type
                Subtype	Feature Code
                Building	2100
                Sky Bridge	2110
                Building Under Construction	5100
                Garage	5110)
              Symbolize by quantity: any quantitative data (year of building
              construction)
                Using the color ramp
                Changing labels
                Changing number of classes
                Different types of classification
                Normalizing

        b. Exercise 2 - selection techniques
            Add Data - Neighborhood Tabulation Areas.
            Select and export only Morningside Heights buildings in two ways:
                Export only Morningside Heights NTA from nynta
                  Select by Location - intersect with Morningside Heights NTA &
                  then export
                  Clip buildings to Morningside Heights NTA & then export

            Export map to illustrator or JPG
              Back to layout view
              Create bookmark
              Add scale + north arrow
              Show how to change scale unit
              Create locator map focusing on Morningside Heights within NYC
              Export or Print
            Export to CAD
              ArcToolbox --> conversion tools --> CAD --> export to CAD
                also show Import from CAD in same place

        c. Exercise 3 - Attribute Table Operations
            Open attribute table of Morningside Heights buildings layer
            ***Talk about how GIS is so cool bc it links attribute info to
            spatial info - powerful for analysis, etc***
            Add "double" field - talk about diff between double, string, long,
            and so on
            Calculate geometry - area [in feet]
            Editor tool - brief demonstration
            ***Flag field calculator here as a powerful too, but say tutorials
            are online***  

            Add Data - NYC population by NTA csv
            ***Mention that csv is preferred to excel for joining***
            Join to total NTA file based on NTAcode field
              ***Mention that join has to be based on a unique field common to
              both files in same type***
              Show common error with non-matching types and how to fix it
              Open attribute table and show the new data in the NTA file
            Export data
              ***Mention you have to export so it's permanently joined***
            Save

        d. Exercise 4 - Working from tabular data to geographic

            Add Data - subway stations csv
            Right-click on layer --> data --> display CY data
            ***mention how it's opposite so the x field is the longitude and
            the y field is the latitude***

            Make a buffer quarter-mile from subway stations [to see what areas
            are more accessible].
            ***here, use the "show help" tool to explain dissolve***
            Alternative way if you just want the features in a zone:
              Select by location - select buildings within quarter mile from
              subway stations

**Session 2:Making a 3D site model of Morningside Heights**
CSR website - show tutorials

USGS & CUGIR site - show how to get data from here and what they are used
for

a. Exercise 1 - 3D Topography of Morningside Heights from point data,
contour lines or raster (for UD only)
    -----point to raster------
    Add "elevation points" shapefile
    Select and export only points in Morningside Heights. Export data.
    Look at metadata on NYC open data portal --> spot elevation has a
    feature code of 300000
    Open attribute table, select by attribute [sub_code = 300000].
    Export data --> exporting only points in Morningside heights with
    spot elevation data

    Customize --> Extensions --> 3D Analyst + Spatial Analyst

    ArcToolbox --> Spatial Analyst Tool --> Interpolation --> Topo to
    Raster
      Change "primary type of input data" from contour to spot
      Change field to elevation and type to point elevation [beside
      layer name]
    Change symbology of raster from classified to stretched

    -----raster to contour-------
    Customize --> Extensions --> 3D Analyst
    ArcToolbox --> 3D Analyst --> Raster Surface --> Contour
      Name "morningsideContour_2ft"
        Set contour interval as 2 (we already know the unit is feet
        because of the coordinate system)
        Z factor remains 1 because we are working with a file in feet
        and generating the contour in feet. If working with a file in
        meters and generating the contour in feet, 0.3048 is Z-factor

    ------2D contour lines to 3D geometry----
    ArcToolbox --> 3D Analyst --> 3D Features --> Feature to 3D by
    attribute
      Input --> morningsideContour_2ft
      Output --> morningsideContour_2ft_3D.shp
      height field --> CONTOUR

    Looks 2D still on there, but if you export to CAD and open in Rhino
    or AutoCAD it'll be 3D / placed on Z-axis

b. Exercise 2 - making and exporting a basic 3D model with building heights
  Copy data from X drive for tutorial 2

  Open ArcScene
  Interface
    Set observer
    Rotate
    Set target
  Add Data[from previous exercise]- buildings_MorningsideHeights_intersect
  Extrude building heights
    Properties --> extrude --> extrusion value: [heightroof]--> add to
    each feature's minimum height
    ***If building heights are insane, check arcScene units is in feet
    Customize --> arcscene properties --> coordinate systems***
  "Fly" through buildings
  **Mention that you can download multipatch files which already have 3D
  info from DCP***
  Check model units --> using coordinate system
  Export scene (3D)
    File --> export scene --> 3D --> to vrml
  Open Rhino
    Change units to feet (to match model)
    Import file
    Rotate bc it imports at 90 degree angle
    Mention that if you want to edit the file, its gonna be huge BUT its
    possible.
    Explode --> MeshToNURB
      Make Edits
    Join
    Save
  ***Mention that you can also export to Google Earth - tutorial on csr
  website***

c. Exercise 3 - Working with topographic surfaces
  Open arcScene

  [creating the topographic surfaces]          
    Add topoMorningsideHeights.tif file [the raster we made from elevation
    points at the end of 2D session]
    Change base heights through elevation from surface
      Base heights
        Floating on a custom surface: the tif file
    Add morningsideContour_2ft [make this 3D]
      Base heights  
        no elevation values from surface
        use a constant value or expression [CONTOUR]
    BUT if you add the morningsideContour_2ft_3D, it automatically gives
    the heights

    Make a TIN (triangulated irregular network) to represent 3D surfaces
    as contiguous, non-overlapping contours
      ArcToolbox --> 3D Analyst tools --> Data management --> TIN -->
      createTIN
        Set coordinate system & destination of file
        Height field = CONTOUR
        (surface) type = soft line (for a gradual break in slope)
        ok
      Properties --> uncheck edge types to hide lines
      Can change symbology to show themes.In symbology, click "add" button
      ***people can play around here with showing percentage slope,
      elevation, etc***

  [draping roads, buildings, etc on TIN]
    Add lionMorningsideHeights shapefile
    For properties of the roads and buildings shapefiles -->
      Base heights
        Floating on a custom surface: TIN layer
      --Change extrusion of building to be from base height?--

  [draping an orthoimg on TIN ]
    Add raster image (TIF) to arcScene
    Select YES to build pyramids so it loads faster
    Properties -->
      Base heights
        Floating on a custom surface: TIN layer

  Export (only one layer at a time bc huge files)
    File --> export scene --> 3D
    same process as before

  ***download files on the X drive prior***
  [working with topo from CUGIR/USGS]
    add CUGIR 7.5 minutes topographic file - DEM
      Properties -->
        Base heights
          Floating on a custom surface
    add USGS landsat file
      Properties -->
        Base heights
          Floating on a custom surface
