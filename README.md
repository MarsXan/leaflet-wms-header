# leaflet-wms-header

It's a simple plugin for `leaflet.js` that allows setting custom headers for WMS interface.

It works with javascript and typescript without any dependencies!

> Based on [this idea](https://github.com/Leaflet/Leaflet/issues/2091#issuecomment-302706529)

## Usage

### Javascript

1. install using npm or [🔽 download here](https://raw.githubusercontent.com/map-ir/leaflet-wms-header/master/index.js)

```sh
$ npm install leaflet leaflet-wms-header --save
```

2. add the javascript to your project:

```html
<!-- Assuming your project root is "../" -->
<script src="../node_modules/leaflet/dist/leaflet.js"></script> 
<script src="../node_modules/leaflet-wms-header/index.js"></script> 
```

3. use it like so:

```js
// YOUR LEAFLET CODE

var wmsLayer = L.TileLayer.wmsHeader(
    'https://GEOSERVER_PATH/geoserver/wms?',
    {
        layers: 'ne:ne',
        format: 'image/png',
        transparent: true,
    },
    [
        { header: 'custom header', value: 'text/plain'},
        { header: 'x-api-key', value: '<your api key>' },
    ]
).addTo(map);
```


### Typescript

1. install using npm or [🔽 download here](https://raw.githubusercontent.com/map-ir/leaflet-wms-header/master/index.d.ts)

```sh
$ npm install leaflet @types/leaflet leaflet-wms-header --save
```

2. use it like this:

```ts
import * as L from 'leaflet';
import 'leaflet-wms-header';

// YOUR LEAFLET CODE

let wmsLayer: L.TileLayer.WMSHeader = L.TileLayer.wmsHeader(
    'https://GEOSERVER_PATH/geoserver/wms?',
    {
        layers: layers,
        format: 'image/png',
        transparent: true,
    }, [
        { header: 'Authorization', value: 'JWT ' + MYAUTHTOKEN },
        { header: 'content-type', value: 'text/plain'},
    ]
).addTo(map);
```
3. or you can use it like this:


```ts
import * as L from 'leaflet';
import 'leaflet-wms-header';

// YOUR LEAFLET CODE

leafLetOptions;

constructor() {
    const wmsLayer: L.TileLayer.WMSHeader = new L.TileLayer.WMSHeader(
      'https://map.ir/shiveh',
      {
        layers: 'Shiveh:Shiveh',
        format: 'image/png',
        transparent: true,
      }, [
        {header: 'x-api-key', value: MAP_IR_TOKEN}
      ]
    );
    this.leafLetOptions = {
      layers: [
        wmsLayer
      ]
    };
  }
```
```html
<div
     [leafletOptions]="leafLetOptions"
     leaflet
     class="map"
     ></div>
```
