<script>
import {
  OptionsMixin,
  ControlMixin,
  propsBinder,
  optionsMerger
} from 'vue2-leaflet';
import 'leaflet.polylinemeasure/Leaflet.PolylineMeasure.css';
import 'leaflet.polylinemeasure/Leaflet.PolylineMeasure.js';
export default {
  name: 'LControlPolyLineMeasure',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  mounted() {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);

    this.mapObject = new L.control.polylineMeasure(options);
    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render() {
    return null;
  },
};
</script>