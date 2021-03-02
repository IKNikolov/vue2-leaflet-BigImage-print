<template>
  <div style="height: 100%; width: 100%">
    <l-map
      style="height: 600px"
      :center="mapCentre"
      :zoom="mapZoom"
      ref="map"
    >
      <l-tile-layer
        :url="tileUrl"
        :attribution="tileAttribution"
      />
      
      <l-control-area-measure :options="areaMesureOptions" />
      <l-control-poly-line-measure :options="polylineOptions" />
      <l-control-fullscreen position="topleft" :options="fullscreenOptions" />
      <l-control-print :options="printOptions"  />
      <l-control-history :options="historyOptions"  />
      <l-control-geo-search :options="geoSearchOptions" :providerOptions="providerOptions"  />
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
import LControlPolyLineMeasure from "./components/LControlPolyLineMeasure.vue";
import LControlAreaMeasure from "./components/LControlAreaMeasure.vue";
import LControlHistory from "./components/LControlHistory.vue";
import LControlGeoSearch from "./components/LControlGeoSearch.vue";
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