<script>
import { OptionsMixin, ControlMixin } from "vue2-leaflet";
//import 'leaflet.ScaleFactor/leaflet.scalefactor.min.css';
//import 'leaflet.ScaleFactor/leaflet.scalefactor.js';
export default {
  name: "LControlScaleFactor",
  mixins: [ControlMixin, OptionsMixin],
  created() {
    let recaptchaScript = document.createElement("script");
    recaptchaScript.setAttribute(
      "src",
      "https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"
    );
    document.head.appendChild(recaptchaScript);

    let recaptchaScript2 = document.createElement("script");
    recaptchaScript2.setAttribute(
      "src",
      "https://rawgit.com/MarcChasse/leaflet.ScaleFactor/master/leaflet.scalefactor.min.js"
    );
    document.head.appendChild(recaptchaScript2);

    let recaptchaScript3 = document.createElement("link");
    recaptchaScript3.setAttribute(
      "href",
      "https://rawgit.com/MarcChasse/leaflet.ScaleFactor/master/leaflet.scalefactor.min.css"
    );
    recaptchaScript3.setAttribute("rel", "stylesheet");
    recaptchaScript3.setAttribute("type", "text/css");
    document.head.appendChild(recaptchaScript3);
  },
  mounted() {
    let internval = setInterval(() => {
      if (typeof L.control.scalefactor != "undefined") {
        this.mapObject = new L.control.scalefactor(this.options);
        this.mapObject.addTo(this.$parent.mapObject);
        clearInterval(internval);
      }
    }, 1000);
    //
  },
  render() {
    return null;
  },
};
</script>