<script>
import {
  OptionsMixin,
  ControlMixin,
  propsBinder,
  optionsMerger
} from 'vue2-leaflet';

import 'leaflet-bing-layer/leaflet-bing-layer.js';

export default {
  name: 'LBingMapsLayer',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  props: {
    bingMapsKey: {
      type: String,
      require: true
    }
  },
  mounted() {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);

    console.log(options);
    options.bingMapsKey = this.bingMapsKey;

    this.mapObject = new L.tileLayer.bing(options);

    propsBinder(this, this.mapObject, this.$options.props);
    //this.mapObject.addTo(this.$parent.mapObject);
    this.$emit('map-object', this.mapObject);
  },
  methods: {
  },
  render() {
    return null;
  },
};
</script>