<script>
import { Icon } from "leaflet";
import {
  OptionsMixin,
  ControlMixin,
  propsBinder,
  optionsMerger
} from 'vue2-leaflet';
import L from 'leaflet';
import { GeoSearchControl, OpenStreetMapProvider, GoogleProvider } from 'leaflet-geosearch';


delete Icon.Default.prototype._getIconUrl;

Icon.Default.mergeOptions({
  iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png').default,
  iconUrl: require('leaflet/dist/images/marker-icon.png').default,
  shadowUrl: require('leaflet/dist/images/marker-shadow.png').default,
});


export default {
  name: 'LControlGeoSearch',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  mounted() {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);
    
    options.provider = new OpenStreetMapProvider(this.providerOptions ?? {});

    const searchControl = new GeoSearchControl(options);

    this.$parent.mapObject.addControl(searchControl);

    //this.mapObject = new L.addControl(searchControl);
    //propsBinder(this, this.mapObject, this.$options.props);
    //this.mapObject.addTo(this.$parent.mapObject);
    //this.mapObject.addTo(this.$parent.mapObject);
  },
  render() {
    return null;
  },
};
</script>
<style>
    @import '~leaflet-geosearch/dist/geosearch.css';
    /*
    .geosearch.leaflet-bar input {
        width: 87%;
        height: 26px;
    }

    .geosearch.leaflet-bar a.reset {
        display: inline-block;
    }
    */
</style>