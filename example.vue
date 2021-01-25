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
      <l-control-big-image :options="printOptions"  />
    </l-map>
  </div>
</template>

<script>
import L from 'leaflet';
import {
  LMap,
  LTileLayer
} from 'vue2-leaflet';
import LControlBigImage from './LControlBigImage.vue';
export default {
  components: {
    LMap,
    LTileLayer,
    LControlBigImage,
  },
  data() {
    return {
      mapCentre: [51, -114],
      mapZoom: 10,
      tileUrl: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      tileAttribution: '&copy; <a href="//osm.org/copyright">OpenStreetMap</a> contributors',
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