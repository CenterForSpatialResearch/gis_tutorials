# Working with Projections and Geographic Coordinate Systems in ArcGIS

*This tutorial will cover how to project data, how to change coordinate systems, and how to define missing projections in ArcGIS*

A data set's projection tells ArcGIS where the data is located on the Planet Earth. Without a projection, the data could be located anywhere. This is a critical concept to understand as you will encounter data without projections defined, or data with different projections than what you are working in or would desire to be working in. It is not essential but often desirable that all your data be in the same projection if you are performing analyses on the data.

We use projections because the Earth basically approximates an ellipsoid. However, when creating maps and GIS data files, we are viewing the Earth's surface in only 2 dimensions. Thus, we must have a way to convert the curved surface of the Earth to a flat plane. A projection is simply the mathematical process by which geographic locations are converted from a 3D sphere to a 2D flat surface.

There are 3 main types of projections:

  * Equal Area Projections - preserve the area of features by assigning them an area on the map that is proportional to their area on the Earth
  *Conformal Projections - preserve the shape of small features and show directions correctly (i.e. State Plane projections)
  *Equidistant Projections - preserve distances to places from one or two points

## Determining a Projection

![t17-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-0.png)

Open ArcMap. Add data into your dataset. Right click on `Properties` and navigate to the `Source` tab. This is where we can determine the projection of a dataset.

Here you can see information about the Projection, and we see that our datset for the boundry of New York City is in a Geographic Coordinate System defined as NAD 1983 New York Long Island State Plane Projection FIPS 3104 Feet. 

![t17-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-1.png)

If we load another file, in this case the subway routes of New York City, we see that they are in a Geographic Coordinate System defined as GCS_North_American_1983.

While these two datasets are in different Geographic Coordinate Systems, they are previewed correctly in ArcGIS. ArcGIS uses the projection of the first dataset that you import in the map.

## Projecting Spatial Data from One Projection to Another

For this exercise, we will project the subway data that is in GCS_North_American_1983 to the NAD 1983 New York Long Island State Plane Projection FIPS 3104 Feet projection, so that it matches with the rest of the data.

![t17-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-2.png)

Navigate to `ArcToolbox`, the red toolbox icon in the menu bar. Under `Data Management Tools` go to `Projections and Transformations`

![t17-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-3.png)

This will open the `Project` tool that will allow us to transform our data from one projection to another. In this case, our input dataset will be the subway routes and we will specify an output location.

![t17-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-4.png)

Under `Output Coordinate System` click on the pointer finger to the right to launch the Output Coordinate System wizard. If you already have a layer that contains the projection you would like to use, you can navigate under `Layers` and find your projection, here the NAD 1983 New York Long Island State Plane Projection FIPS 3104 Feet. If you want to project to a coordinate system not already in your map you can similarly find this projection using the `Projected Coordinate Systems` folder and navigate to your coordinate system of interest. Click `OK` to project the data.

NOTE: each folder contains the projection (i.e. State Plane) and subfolders containing the Datum (i.e. NAD 1983 feet). Coordinate Systems are composed of both their projections and datums.

![t17-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-5.png)

You may be prompted to add the data to your map or you will have to add the data to your map from your output location. We see here that the data was successfully converted to the NAD 1983 New York Long Island State Plane Projection FIPS 3104 Feet Projected Coordinate System.

## Defining a Projection

In some cases, the data you download might be missing a projection and you will have to define the projection of the data.

![t17-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-6.png)

When you add this data, a dialog box will appear warning you about the Unknown Spatial Reference.

Assuming that you know what Coordinate System that is associated with the data, you can define the coordinate system.

![t17-7.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-7.png)

If we look now at the `Layer Properties` we see the `Coordinate System` is `<Undefined>`.

![t17-8.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-8.png)

To define the projection, to to `ArcToolbox` > `Projections and Transformations` > `Define Projection`.

![t17-9.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-9.png)

In the `Define Projection` dialog box, choose your input file from the dropdown under `Input Dataset or Feature Class`.

Under `Coordinate System` click on the pointer finger to launch the `Spatial Reference Properites` and find your appropriate projection. We will use the same projection in our map, the NAD 1983 New York Long Island State Plane Projection FIPS 3104 Feet Projected Coordinate System.

Click `Ok` and `OK` and your dataset will now have a defined projection. 

![t17-10.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-10.png)

Navigate to the `Layer Properties` of your dataset and you will see that it now has the Projected Coordinate System you specified.

You may have noticed that the soils dataset did not move its location when you changed its projection. This is because ArcMap draws all data layers that already have their Projections Defined in the current Data Frame’s projection. These already defined layers are projected on-the-fly into the current Data Frame’s projection and thus are displayed as if they are all the same Projection and Datum. Therefore the data is displayed in the Data Frame as if their projections are the same, even if they are different. A rule of thumb is project all your datasets into the same common projection to minimize conflicts when you are doing your research.

## Defining the Projection of a Data Frame

The Data Frame of your Map is in a specified Coordinate System. This coordinate system will use the first piece of data that you import. You can change the Coordinate System of your Data Frame at any time.

*NOTE: This will physically alter the appearance of your map, possibly distorting your data if you do not choose an appropriate coordinate system.*

![t17-11.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-11.png)

Right-click on the Data Frame named `Layers`. In the `Data Frame Properties` window go to the tab named `Coordinate System`. You can see here that our current coordinate system is NAD 1983 New York Long Island State Plane Projection FIPS 3104 Feet. We can change this to another coordinate system if we want.

![t17-12.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_17/t17-12.png)

We will choose the GCS North American 1983 coordinate system. Note that this will distort the map in this case largely stretching it horizontally.

It is important that you choose appropriate Coordinate Systems when working with Spatial Data.
