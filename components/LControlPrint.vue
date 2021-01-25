<script>
import {
  OptionsMixin,
  ControlMixin,
  propsBinder,
  optionsMerger
} from 'vue2-leaflet';
import 'leaflet.browser.print/dist/leaflet.browser.print.min.js';
export default {
  name: 'LControlPrint',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  mounted() {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);

    let printOptions = {};
    if(typeof options.options != 'undefined' && Array.isArray(options.options.printModes)) {
      let newPrintModes = [];
      options.options.printModes.forEach((value, index) => {
        if (value.type == 'all'){
          newPrintModes.push(L.control.browserPrint.mode.landscape(value.name, "tabloid"));
        } else if (value.type == 'landscape'){
          newPrintModes.push(L.control.browserPrint.mode.landscape(value.name));
        } else if (value.type == 'portrait'){
          newPrintModes.push(value.name);
        } else if (value.type == 'custom'){
          newPrintModes.push(L.control.browserPrint.mode.custom(value.name, "B5"));
        }
      });

      options.options.printModes = newPrintModes;
      printOptions = options.options;
    }

    
    this.mapObject = new L.control.browserPrint(printOptions)
    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render() {
    return null;
  },
};
</script>