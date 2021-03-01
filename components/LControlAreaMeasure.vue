<script>
import {
  OptionsMixin,
  ControlMixin,
  propsBinder,
  optionsMerger
} from 'vue2-leaflet';
import 'leaflet-measure/dist/leaflet-measure.css';
import 'leaflet-measure/dist/leaflet-measure.js';
export default {
  name: 'LControlAreaMesure',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  mounted() {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);

    this.mapObject = new L.Control.Measure(options);
    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render() {
    return null;
  },
};
</script>

<style>
  .leaflet-control-measure-interaction a.cancel,
  .leaflet-control-measure-interaction a.finish,
  .leaflet-control-measure-interaction a.start {
    width: auto !important;
    text-align: left !important;
    display: inline !important;
  }
</style>