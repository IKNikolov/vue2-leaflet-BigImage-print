# Leaflet simple tools for vue2

Simple vue2 package to be possible using of few packages in vue projects.

## PACKAGES

[Leaflet.fullscreen](https://github.com/Leaflet/Leaflet.fullscreen)

[Map Print Plugin for Leaflet.js](https://github.com/Igor-Vladyka/leaflet.browser.print)

[Leaflet.PolylineMeasure](https://github.com/ppete2/Leaflet.PolylineMeasure)

[leaflet-measure](https://github.com/ljagis/leaflet-measure)

[Leaflet-History Control](https://github.com/cscott530/leaflet-history)

[Leaflet.GeoSearch](https://github.com/smeijer/leaflet-geosearch)


## Usage

You can read the documentation of the packages above and use their options like in the example below.

### IMPORTANT FOR [Map Print Plugin for Leaflet.js](https://github.com/Igor-Vladyka/leaflet.browser.print)

I replaced the original print modes option from the documentation of the print plugin. Please see the printModes in the example below.

I added additional options to be possible to have [L.control.scale()](https://leafletjs.com/reference-1.7.1.html#control-scale) in the printed map. You can see the example below in printOptions.

### IMPORTANT FOR Leaflet.GeoSearch

I used only OpenStreetMapProvider for now. If someone wants to use this package and other Leaflet.GeoSearch provider just writes an issue.

```html
<script>
import L from 'leaflet';
import {
  LMap,
  LTileLayer,
  LControlScale
} from 'vue2-leaflet';
import { 
  LControlPrint, 
  LControlFullscreen, 
  LControlPolyLineMeasure, 
  LControlAreaMeasure, 
  LControlHistory 
} from 'vue2-leaflet-inikolov-simple-tools';
export default {
  components: {
    LMap,
    LTileLayer,
    LControlPrint,
    LControlFullscreen,
    LControlPolyLineMeasure,
    LControlAreaMeasure,
    LControlHistory,
    LControlGeoSearch,
    LControlScale
  },
  data() {
    return {
      mapCentre: [51, -114],
      mapZoom: 10,
      tileUrl: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      tileAttribution: '&copy; <a href="//osm.org/copyright">OpenStreetMap</a> contributors',


      fullscreenOptions: {
        title: {
          'false': 'Switch to full-screen view',
          'true': 'Exit full-screen mode',
        },
      },


      printOptions: {
        title: 'Just print me!',
        documentTitle: 'Map printed using leaflet.browser.print plugin',
        closePopupsOnPrint: false,
        printModes: [
          {"type": 'all', "name": 'All'},
          {"type": 'landscape', "name": 'Landscape'},
          {'type': 'portrait', 'name': 'Portrait'},
          {'type': 'custom', 'name': 'Select'}
        ],
        manualMode: false,
        showScale: true,
        scaleOptions: {
          metric: true,
          imperial: false,
          position: "bottomleft"
        }
      },


      polylineOptions: {
        position: 'topleft',
        showClearControl: true,
        showUnitControl: true
      },


      areaMesureOptions: {
        position: 'topleft'
      },


      historyOptions: {
        backText: 'Back',
        forwardText: 'Forward',
      },


      geoSearchOptions: {
        position: 'topright',
        style: 'bar',
      },

      
      providerOptions: {
        language: 'bg',
        region: 'bg',
      },

    };
  },
  methods: {

  }
};
</script>

<style>
@import '~leaflet/dist/leaflet.css';
</style>

```