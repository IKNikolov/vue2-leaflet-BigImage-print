<script>
import { OptionsMixin, ControlMixin, propsBinder, optionsMerger } from 'vue2-leaflet';
import 'leaflet.bigimage/dist/Leaflet.BigImage.min.js';
import 'leaflet.bigimage/dist/Leaflet.BigImage.min.css';
export default {
  name: 'LControlBigImage',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  mounted () {
   const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);

    this.mapObject = new L.Control.BigImage(options);
    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render () {
    return null;
  },
};
</script>