#Setting up the ArcGIS Environment

##ArcGIS Basics
ArcGIS is made up of three main programs: ArcScene for 3D mapping, ArcMap for 2D mapping, and ArcCatalog for file management. Files can be copied through your local system or through ArcCatalog, but ArcCatalog is the more stable way to move files from one location to another. The format ArcMap files are saved in is .mxd.

The most common (and simplest) files for mapping are shapefiles, which are actually a composite of four to six different file [types](http://webhelp.esri.com/arcgisdesktop/9.3/index.cfm?topicname=Shapefile_file_extensions). The most common are outlined below:
  *required
    *.shp: main file that stores geometry 
    *.shx: index file
    *.dbf: database file that stores attribute information 
  *optional
    *.prj: projection file
    *.xml: metadata
    *.sbn: spatial index
    *.sbx: spatial index

Shapefiles can represent geographic data through lines, points and polygons. Shapefiles contain attribute as well as geographic information, which means that each line, point or polygon can have particular numeric or text attributes attached to it. 

A geodatabase can hold point, polygon and line information as well as attribute information in one large file, instead of multiple files as is the case with shapefiles. Geodatabases can be great for keeping files organized, but its contents cannot be accessed legibly through the Windows Explorer. ArcCatalog is necessary for managing geodatabases. 

![t25-0.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-0.png)

As a rule of thumb, do not have spaces in any file or folder names pertaining to the project to avoid any errors. 


##Working with the X drive and ArcCatalog

ArcCatalog only shows one file, instead of the collection of files that constitute a shapefile. Windows Explorer, on the other hand, shows all the files associated with each shapefile. To set a home folder for your project, click the 'connect to folder' button and select the folder(s) you will be using for your ArcMap project. Clicking the “launch ArcMap” button opens ArcMap with these connections already intact.

![t25-1.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-1.png)
![t25-2.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-2.png)

[Connect to the X drive](https://github.com/CenterForSpatialResearch/gis_tutorials/blob/master/21_Connecting_to_X_Drive.md) from your computer and copy files to the local C: drive using Windows Explorer or ArcCatalog (the latter reduces the odds of files breaking). To do so using ArcCatalog, click the connect to folder button on the toolbarand connect to both your local folder and the X drive. Right-click on the files you wish to copy and select copy. Navigate to the folder you are copying to, right-click the folder name and click paste. 

![t25-3.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-3.png)
![t25-4.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-4.png)

##Working with ArcMap 

When you open up ArcGIS, you will be prompted to either open an existing file or start a new file. 
![t25-5.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-5.png)

If you select the latter option, you will have the option to set a new default geodatabase. While this is not mandatory, it is best practice to do so especially if you will be working with geodatabases. Select the 'go to folder' button beside the address bar, and then you can add a folder that ArcGIS automatically associates with the project with the 'connect to folder' button. Finally, make a new geodatabase (or select an existing one) using the new geodatabase button.

![t25-6.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-6.png)
![t25-7.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-7.png)
![t25-8.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-8.png) 
![t25-9.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-9.png)

ArcMap works by linking shapefiles and geodatabases in an mxd file. To avoid these links getting broken, go to 'File —> Map Document Properties —> Store Relative Pathnames'. 
![t25-10.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-10.png)
![t25-11.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-11.png)

ArcCatalog, ArcToolbox and Search are powerful tools accessible from ArcMap. Clicking on any of these from “windows” in the toolbar adds it to the side of the data frame. Using ArcCatalog, you can rename folders, disconnect from folders and perform other operations by right-clicking on a file or folder name. You can access ArcMap tools using ArcToolbox, and search for those tools using Search. This search function is especially useful because while it is often easy to forget which folder in ArcToolbox the “Clip” tool is stored under. 

![t25-12.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-12.png)
![t25-13.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-13.png)
![t25-14.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-14.png)
![t25-15.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-15.png)

The 'Results' window is a handy tool to be aware of - you can view 'error messages' or 'warnings', see how long an operation takes, and rerun a tool from this window.
![t25-16.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-16.png)
![t25-17.png](https://github.com/tolaoniyangi/gis_tutorials/blob/master/Images/Tutorial_25/t25-17.png) 
