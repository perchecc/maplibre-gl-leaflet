**Note: this tool is experimental and is not actively supported by Maplibre. For support, please open an issue in this repository.**

## Maplibre GL Leaflet

This is a binding from [Maplibre GL JS](https://www.mapbox.com/mapbox-gl-js/api/) to the familiar
[Leaflet](http://leafletjs.com/) API.

## Code example

```javascript
var map = L.map('map').setView([38.912753, -77.032194], 15);
L.marker([38.912753, -77.032194])
    .bindPopup("Hello <b>Leaflet GL</b>!<br>Whoa, it works!")
    .addTo(map)
    .openPopup();
var gl = L.maplibreGL({
    style: 'mapbox://styles/mapbox/bright-v8'
}).addTo(map);
```

Note that you can use any vector tile source useable by maplibre-gl. For instance, you can use [OSM2VectorTiles](http://osm2vectortiles.org/) with:

```javascript
var gl = L.maplibreGL({
 style: 'https://api.maptiler.com/maps/topo/style.json?key=<YOUR_MAPTILER_API_KEY>'
}).addTo(map);
```

Once you have created the leaflet layer, the maplibre-gl map object can be accessed using

```javascript
gl.getMaplibreMap()....
// add a source to the maplibre-gl layer
gl.getMaplibreMap().addSource({...})
```

## Live examples

[Basic example](http://rawgit.com/mapbox/mapbox-gl-leaflet/master/examples/basic.html)

[Cluster example](http://rawgit.com/mapbox/mapbox-gl-leaflet/master/examples/cluster.html)

[Map events example](http://rawgit.com/mapbox/mapbox-gl-leaflet/master/examples/events.html)

Code for these examples is hosted in the [examples folder](https://github.com/mapbox/mapbox-gl-leaflet/tree/master/examples)

## Installation

Add a script tag referencing mapbox-gl-leaflet after adding leaflet and mapbox-gl-js in your website:

```html
<!-- Leaflet -->
<link rel="stylesheet" href="leaflet.css" />
<script src="leaflet.js"></script>

<!-- Mapbox GL -->
<link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.5.0/maplibre-gl.css' rel='stylesheet' />
<script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.5.0/maplibre-gl.js'></script>

<script src="leaflet-maplibre-gl.js"></script>
```

You can also use Unpkg as a CDN using:

```html
<script src="https://unpkg.com/mapbox-gl-leaflet/leaflet-maplibre-gl.js"></script>
```

## Motivation

This project makes it possible to easily add a mapbox-gl-js layer in your Leaflet map. When using mapbox-gl-leaflet, you won't be able to use some of the mapbox-gl-js features.
Here are the main differences between a "pure" mapbox-gl-js map and a Leaflet map using mapbox-gl-leaflet:

- No rotation / bearing / pitch support
- Slower performances: When using mapbox-gl-leaflet, mapbox-gl-js is set as not interactive. Leaflet receives the touch/mouse events and updates the mapbox-gl-js map behind the scenes. Because mapbox-gl-js doesn't redraw as fast as Leaflet, the map can seem slower.

On the bright side, the mapbox-gl-leaflet binding will allow you to use all the leaflet features and plugins.

If you only need the mapbox-gl-js features ([adding a map with a mapbox-style, adding a GeoJSON, etc.](https://www.mapbox.com/mapbox-gl-js/examples/)), you are probably better off using it directly.

## API Reference

[API Reference](API.md)

## Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/mapbox/mapbox-gl-leaflet/issues) to report any bugs or file feature requests.
You can fork this [jsfiddle template](https://jsfiddle.net/fnicollet/9w9er53v/) to reproduce a bug, then share the URL of your fork in the GitHub issue.

## Licence

ISC © [Mapbox](https://github.com/mapbox)
