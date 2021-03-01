<script>
import {
  OptionsMixin,
  ControlMixin,
  propsBinder,
  optionsMerger
} from 'vue2-leaflet';
import '@fortawesome/fontawesome-free/css/all.min.css';
import 'leaflet-history/dist/leaflet-history.css';
import 'leaflet-history/dist/leaflet-history.js';
export default {
  name: 'LControlHistory',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  mounted() {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);

    this.mapObject = new L.HistoryControl(options);
    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render() {
    return null;
  },
};
</script>
<style>
    .history-control.leaflet-bar.horizontal a {
        width: auto;
        padding: 0 5px 0 5px;
    }
</style>