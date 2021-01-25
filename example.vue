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
import LControlPrint from "./components/LControlPrint.vue";
import LControlFullscreen from "./components/LControlFullscreen.vue";
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