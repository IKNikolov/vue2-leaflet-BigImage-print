# Leaflet simple tools for vue2

Simple vue2 package to be possible using of few packages in vue projects.

## PACKAGES

[Leaflet.fullscreen](https://github.com/Leaflet/Leaflet.fullscreen)

[Map Print Plugin for Leaflet.js](https://github.com/Igor-Vladyka/leaflet.browser.print)


## Usage

You can read the documentation of the packages above and use their options like in the example below (fullscreenOptions and printOptions).

### IMPORTANT FOR printModes

I replaced the original print modes option from the documentation of the print plugin. Please see the printModes in the example below.

```html
<template>
  <div style="height: 100%; width: 100%">
    <l-map
      style="height: 400px"
      :center="mapCentre"
      :zoom="mapZoom"
      ref="map"
    >
      <l-tile-layer
        :url="tileUrl"
        :attribution="tileAttribution"
      />
      <l-control-fullscreen position="topleft" :options="fullscreenOptions" />
      <l-control-print :options="printOptions"  />
    </l-map>
  </div>
</template>

<script>
import L from 'leaflet';
import {
  LMap,
  LTileLayer
} from 'vue2-leaflet';
import { LControlPrint, LControlFullscreen } from 'vue2-leaflet-inikolov-simple-tools';

export default {
  components: {
    LMap,
    LTileLayer,
    LControlPrint,
    LControlFullscreen
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
        manualMode: false
      }
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