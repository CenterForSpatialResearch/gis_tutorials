# Connecting to the X drive from the GSAPP computers

The X Drive has a wealth of information primarily about New York City but also some other global locations. All school computers should automatically be connected to the X drive, but in the event it is missing, here are the steps to reconnect:
* Double click on MyComputer from your desktop. If you see the `X:\` drive listed, then you will not need to reconnect.
* If it is not listed, click on the `Tools` pulldown menu and select `Map Network Drive`.
* Expand the Architecture network, then scroll down and expand the New York network.
* Find the GIS folder, click on it and press `OK`. This returns you to the previous window where you select `Finish`. The `X:\` drive will open in a new window and you are now connected.

### Caution!
* Do not run GIS files from the `X:\` drive. Running these files of the network will slow down your work (and everyone else's) and you will not be able to save any changes you make. It is recommended that you use ArcCatalog to find the files you wish to use and to then make a copy of them on your local scratch drive.
* Shape files, the main GIS file format, are made up of a series of files. If you only copy the `.shp` you will not have the entire file. Shapefiles are made up of `.shp`, `.shx`, `.dbf`, `.sbx` extensions. Copy everything that has the same name as the `.shp` to be sure that you have all the proper files.
* The `X:\` drive is organized into folders and subfolders as follows: New York City Data US Regional Data - Metropolitan Areas, with a Focus on the Northeast State Data NY Tristate US Cities International
