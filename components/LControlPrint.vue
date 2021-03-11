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
          newPrintModes.push(L.control.browserPrint.mode.portrait(value.name));
        } else if (value.type == 'custom'){
          newPrintModes.push(L.control.browserPrint.mode.custom(value.name, "B5"));
        }
      });

      options.options.printModes = newPrintModes;
      printOptions = options.options;
    }

    
    this.mapObject = new L.control.browserPrint(printOptions);

    if (typeof options.showScale != 'undefined' && options.showScale === true){
      console.log(options.showScale);
      let scaleOptions = options.scaleOptions ?? {};
      this.$parent.mapObject.on("browser-print-start", function(e){
				L.control.scale(scaleOptions).addTo(e.printMap);
			});
      
    }

    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render() {
    return null;
  },
};
</script>