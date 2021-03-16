<script>
import {
  OptionsMixin,
  ControlMixin,
} from 'vue2-leaflet';
import 'leaflet.ScaleFactor/leaflet.scalefactor.min.css';
//import 'leaflet.ScaleFactor/leaflet.scalefactor.js';
export default {
  name: 'LControlScaleFactor',
  mixins: [
    ControlMixin,
    OptionsMixin,
  ],
  created() {
      let recaptchaScript = document.createElement('script')
    recaptchaScript.setAttribute('src', 'https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js')
    document.head.appendChild(recaptchaScript)

    let recaptchaScript2 = document.createElement('script')
    recaptchaScript2.setAttribute('src', 'https://rawgit.com/MarcChasse/leaflet.ScaleFactor/master/leaflet.scalefactor.min.js')
    document.head.appendChild(recaptchaScript2)
  },
  mounted() {
    this.mapObject = new L.control.scalefactor(this.options);
    this.mapObject.addTo(this.$parent.mapObject);
  },
  render() {
    return null;
  },
};

</script>