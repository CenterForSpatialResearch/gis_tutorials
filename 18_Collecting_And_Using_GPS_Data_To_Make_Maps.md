# Collecting and Using GPS Data to Make Maps

*GSAPP has Garmin hand-held GPS receivers available for your use. The model of the devices is the Garmin GPSMap64. Below are instructions for collecting and transfering GPS data to GIS.*

This tutorial uses the Garmin GPSMAP 64, DNR Garmin, and ArcGIS 10.4

## Using the GPS Receiver

![garmin.jpg](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/garmin.jpg)

Turn on the GPS receiver: The power button is the button on the right-hand side of the device. You will use this same button to turn off the device when you are done recording your data. Once the power has been turned on, the receiver will automatically begin to track satellites. 

Note: this particular GPS device does not work indoors. It must always be in an open area outside, with a clear view of the sky.

Choose the `PAGE` button to choose between the `Main Menu`, `Map`, `Compass`, `Trip Computer`, and `Elevation point`. We will choose `Map` to view our present location. You can zoom in and out of the map using the `IN` and `OUT` buttons. You can press `QUIT` at any point to exit a menu option.

## Waypoints

Waypoints are used to store and remember locations that are of interest to the user. They are often used to store intermediate turns and intersections that help define a route to a particular destination.

Storing your present location is the usual way to record a waypoint. To create a waypoint, simply hit the `Mark` button on the bottom left hand corner of the device. Use the scrolling features to edit the Marker symbols and notes, hovering over each item and clicking 'ENTER` if you wish to edit. Scroll to `Done` and press `ENTER`.

 Note: The location you were at the moment you pressed the button is saved in the waypoint information on the form. To consult the data on your waypoint, select the `FIND` button and go to `Waypoints` to see the list of Waypoints you have logged. You can then call up the spatial information on your point or rename it so that you can remember what location/route marker/feature you wanted to mark.

 ## Routes

A Route is a collection of Waypoints that are related in a way that permits you to use them to follow a prescribed course. If you already have a set of waypoints entered that you wish to turn into a route then you can simply use the route page and enter them in whatever order you wish.

Press the `PAGE` buttom and navigate to the `Main Menu`. From the `Main Menu`, select the `Route Planner` option. Select `Create Route` to create a route from your existing waypoints. Select `Select First Point` and navigate to `Waypoints` to see the list of Waypoints you have logged. Select `Use` to calculate the route. Press `QUIT` to save the route.

To add additional Waypoints, proceed in the same fashion until you have selected all of the Waypoints that you would like to add. They are now part of your route and can be uploaded from the device under the designated route name.

## Tracks

Using the `PAGE` button once again, go to the `Main Menu`. Select the `Setup` option. Select the `Tracks` option. This will allow you to continuously record data as you navigate the city. You can change the recording settings and the color of the Tracks that will be displayed on the map.

To view your current track, press `PAGE` and navigate to the `Main Menu`. Go to `Track Manager` and select `Current Track` Select `View Map` to show the current track on the map or `Elevation Plot` to show the elevation plot for the track.

To save the current track, press `PAGE` and navigate to the `Main Menu`. Go to `Track Manager` and select `Current Track`. Select `Save Track` to save the entire track or select `Save Portion` to select a portion of the track.

## Uploading Your Data

![t18-0.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/t18-0.png)

Connect the GPS receiver to the serial port of a your computer. Launch DNR GARMIN. This application is available via the [Minnesota Department of Natural Resources](http://www.dnr.state.mn.us/mis/gis/DNRGPS/DNRGPS.html). This application is available on GSAPP computers in Fayerweather 202.

![t18-1.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/t18-1.png)

`Open the DNR GPS Properties`. By default, the default projection (NAD83_UTMZone15). Make sure that the datum is defined as `WGS 84` and the projection is set to `No Projection`.

![t18-2.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/t18-2.png)

From the top menu, go to `GPS` > `Find GPS` to connect to your device.

![t18-3.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/t18-3.png)

To download Waypoints, go to `Waypoints` > `Download`. Your waypoints will now be displayed in the table.

![t18-4.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/t18-4.png)

To download Tracks, go to `Tracks` > `Download`. Your tracks will now be displayed in the table. These will be imported as points in sequential order of your tracks and can be exported as a line.

![t18-5.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/t18-5.png)

To download Tracks, go to `Tracks` > `Download`. Your tracks will now be displayed in the table. These will be imported as points in sequential order of your tracks and can be exported as a line.

![t18-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/t18-6.png)

To save your data go to `File` > `Save To` > `ArcMap`. Make sure `ESRI Shapefile` is the file type when saving your data.

Saving your data: Make sure you save your data as appropriate data (points, lines, polygons, etc.). When you use Waypoints, you can only download your data as point information. If you select Routes or Tracks, you may use both point or line information.

![t18-6.png](https://github.com/jai2125/gis_tutorials/blob/master/Images/Tutorial_18/t18-6.png)

You can now import your shapefiles into ArcMap. Ensure your data is in the correct projection by exporting the data in the same coordinate system of the `Data Frame`.

You have now created and visualized GPS data from your device in ArcMap.