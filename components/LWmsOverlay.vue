<script>
import {
  OptionsMixin,
  ControlMixin,
  propsBinder,
  optionsMerger
} from 'vue2-leaflet';
import wms from  'leaflet.wms/dist/leaflet.wms.js';
export default {
  name: 'LWmsOverlay',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  props: {
    url: {
      type: String,
      required: true
    }
  },
  mounted() {
    /*
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);
    */

    this.mapObject = new wms.overlay(this.url, this.options);
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