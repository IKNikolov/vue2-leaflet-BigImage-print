<script>
import {
  OptionsMixin,
  ControlMixin,
  propsBinder,
  optionsMerger
} from 'vue2-leaflet';
//import 'leaflet.bigimage/dist/Leaflet.BigImage.min.js';
//import 'leaflet.bigimage/dist/Leaflet.BigImage.min.css';
import 'leaflet.browser.print/dist/leaflet.browser.print.min.js';
export default {
  name: 'LControlBigImage',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  mounted() {
    const options = optionsMerger({
      ...this.controlOptions,
      options: this.options,
    }, this);

    /*
    this.mapObject = new L.Control.BigImage(options);
    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
    */
   /*
    var customActionToPrint = function (context, mode) {
      return function () {
        window.alert("We are printing the MAP. Let's do Custom print here!");
        context._printCustom(mode);
      }
    }
    */
   /*
   {
      title: 'Just print me!',
      documentTitle: 'Map printed using leaflet.browser.print plugin',
      closePopupsOnPrint: false,
      printModes: [
        L.control.browserPrint.mode.landscape("Всичко", "tabloid"),
        //L.control.browserPrint.mode("Alert", "User specified print action", "A6", customActionToPrint, false),
        L.control.browserPrint.mode.landscape(),
        "Portrait",
        //L.control.browserPrint.mode.auto("Automatico", "B4"),
        L.control.browserPrint.mode.custom("Селектиране на зона за принтиране", "B5")
      ],
      manualMode: false
    }
    */
    this.mapObject = new L.control.browserPrint(options)
    propsBinder(this, this.mapObject, this.$options.props);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render() {
    return null;
  },
};
</script>