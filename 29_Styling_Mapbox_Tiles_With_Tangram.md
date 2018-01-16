# Styling Mapbox Tiles with Mapzen's Tangram

[Tangram](https://mapzen.com/products/tangram/) is a great open-source map renderer designed by [Mapzen](https://mapzen.com/) and meant to work primarily with their OpenStreetMap [vector tiles](https://mapzen.com/projects/vector-tiles). It is the way we styled and render the maps for our [Conflict Urbanism: Colombia](c4sr.columbia.edu/conflict-urbanism-colombia) and [Locations of Justice](https://urbanomnibus.net/2017/11/map-location-justice/) projects. However, Mapzen's APIs will shut down on February 1st, 2018, and with them we will loose the ability to style and render their OSM data.

Mapzen has fortunately [outlined multiple alternatives to their APIs](https://mapzen.com/blog/migration/), including running your own version of their tile server and getting basemaps and tiles from other providers such as [Mapbox](https://www.mapbox.com/maps/), [OpenMapTiles](https://openmaptiles.org/), or [Thunderforest](https://thunderforest.com/docs/vector-maps-api/). Here at [C4SR](c4sr.columbia.edu), we have been actively experimenting with these alternatives and will probably implement a couple of different ones in the projects that currently rely on Mapzen's tiles.

This post describes one of our alternatives, probably the easiest we have found, which combines Mapbox tiles with Tangram's styling and rendering. This way you don't have to recreate your style within Mapbox or use other rendering libraries in your code. You just have to hook up your Mapbox tiles to your Tangram's `scene.yaml` file and adjust your style parameters to suit Mapbox's tiles schema.

## Styling Mapbox Tiles with Tangram

The first thing you need to do is to get your API key (or access token) from Mapbox. Once you have your key you should go to the top of your `scene.yaml` file and change your sources. Change your URL to Mapbox's tile server (`https://a.tiles.mapbox.com/v4/mapbox.mapbox-streets-v7/{z}/{x}/{y}.mvt`) and add your access token to the end of the URL (`?access_token=xxx.xxx.xxx`). Your tile source should look something like this:
```yaml
sources:
  mapbox:
    type: MVT
    url: https://a.tiles.mapbox.com/v4/mapbox.mapbox-streets-v7/{z}/{x}/{y}.mvt?access_token=xxx.xxx.xxx
    max_zoom: 16
    tile_size: 512
```

Once this is done, you will be rendering Mapbox's tiles instead of Mapzen's. However, even though Mapbox's tiles are mostly based on OSM data they have a different schema than Mapzen's, which means that you should adjust the code in your `scene.yaml` accordingly.

The most useful resources we found to understand Mapbox's schema were [this page](https://www.mapbox.com/vector-tiles/mapbox-streets-v7/) and [this one](https://www.mapbox.com/studio/tilesets/mapbox.mapbox-streets-v7/). They both contain more or less the same information, just organized a little differently. For example, we see here that the layer containing roads is called `road` as opposed to `roads` (with an 's') or that there is no layer containing the `earth`. In addition, one important difference between the two tilesets is the fact that in Mapbox's tiles, labels are their own independent layers, not included in the respective feature layers.

To add a background layer (the equivalent of an `earth` layer in Mapzen) you can add a background color in your `.html` file. In the line where you create your `map` div, just add a style line with the background color. Ours looks like this:
```html
<div id="map" style="width: 1024px; height: 576px; background-color: white;">
```

The rest of the styling is fairly straight forward. Here's an example of a style for primary and secondary roads. The first one is the original using **Mapzen** tiles:
```yaml
roads:
    data: {source: mapzen}
    major-roads:
      filter:
        kind: [major_road]
        $zoom: {min: 12, max: 20}
      draw:
        lines:
          order: 4
          color: '#F2F2F2'
          width: [[12, 1px], [13, 2.5px], [14, 4.5px], [15, 5.5px], [16, 7.0px], [19, 14m]]
          outline:
            color: '#D9D9D9'
            width: [[12, 0px], [14, 1.25px], [16, 1px], [18, 2px]]
```
This one is the new one using **Mapbox** tiles:
```yaml
road:
    data: {source: mapbox}
    major-roads:
      filter:
        class: [trunk, primary, secondary]
        $zoom: {min: 12, max: 20}
      draw:
        lines:
          order: 4
          color: '#F2F2F2'
          width: [[12, 1px], [13, 2.5px], [14, 4.5px], [15, 5.5px], [16, 7.0px], [19, 14m]]
          outline:
            color: '#D9D9D9'
            width: [[12, 0px], [14, 1.25px], [16, 1px], [18, 2px]]
```
The two main differences are that in Mapzen the layer is called `roads` (with and 's' at the end) and in Mapbox it is called `road`, and that in Mapzen, you can filter the layer using the `kind` attribute, while in Mapbox, you use primarily the `class` attribute to filter features.

Finally, as I said before, in Mapbox you need to add separate layers for the labels. These work similarly than other features but just need to be fully independent. Here is an example of a label layer for cities in **Mapbox**:
```yaml
place_label:
  data: {source: mapbox}
  otherCities:
    filter:
      type: [city]
    draw:
      text:
        move_into_tile: false
        order: 7
        font:
          family: 'Neue Haas Unica W01 Regular'
          weight: 300
          size: [[12,8px],[13,9px],[14,10px],[15,11px],[16,12px]]
          fill: '#A6A6A6'
```
One important thing to note here is the `move_into_tile: false` condition. If you don't add this condition, you will probably notice how multiple labels appear for the same feature. This is because Mapbox's tiles are buffered while Mapzen's are not. The `move_into_tile: false` statement prevents this repetition from happening.

That's about it. With this you should be able to use Mapbox tiles while still styling and rendering them with Mapzen's Tangram. Some small things might be a little different but from the alternatives we've experimented with, this has been the easiest one.

### Adding Terrain Tiles Directly from AWS

In addition, if your map also uses Mapzen's terrain tiles you can easily just link it directly to the AWS's URL, bypassing Mapzen's APIs. In the `sources` section of your `scene.yaml` file, just change your terrain URL. Here's how mine looks:
```yaml
sources:
    normals:
        type: Raster
        url: https://s3.amazonaws.com/elevation-tiles-prod/normal/{z}/{x}/{y}.png
        max_zoom: 15
```

### Thanks

Thanks to [Ruatara Paapu](https://gis.stackexchange.com/users/91712/ruatara-paapu) and to [Nathaniel Kelso](https://twitter.com/kelsosCorner) for their help. And of course, thanks to [Mapzen](https://mapzen.com/) for creating these great tools in the first place.
