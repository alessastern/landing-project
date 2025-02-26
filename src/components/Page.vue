<template>
  <Header @link-click="setFocus" />
  <div class="container">
    <Gallery ref="Home" :slides="slides" :interval="3000" controls indicators />
    <h2 class="title">i made dis</h2>
    <Text ref="About" :about="about" />
    <FeedbackForm ref="Feedback" />
  </div>
</template>

<script>
import Text from "./Text.vue";
import Header from "./Header.vue";
import Gallery from "./Gallery.vue";
import FeedbackForm from "./FeedbackForm.vue";
export default {
  components: { Gallery, FeedbackForm, Header, Text },
  methods: {
    setFocus(e) {
      this.$refs[e].$el.scrollIntoView({ block: "center", behavior: "smooth" });
    },
  },
  data() {
    return {
      slides: [
        "https://c4.wallpaperflare.com/wallpaper/586/603/742/minimalism-4k-for-mac-desktop-wallpaper-preview.jpg",
        "https://c4.wallpaperflare.com/wallpaper/448/174/357/neon-4k-hd-best-for-desktop-wallpaper-thumb.jpg",
        "https://www.pixelstalk.net/wp-content/uploads/images6/5K-Wallpaper-HD-Free-download.jpg",
        "https://4kwallpapers.com/images/walls/thumbs_3t/14482.jpg",
      ],
      about:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit.\nDonec cursus rhoncus diam, ut scelerisque mauris sollicitudin id. Mauris accumsan sapien orci, vel semper leo commodo dictum. Integer tincidunt enim ac facilisis commodo. Curabitur pretium lectus odio, eget faucibus nulla sollicitudin at. Vivamus nisi neque, elementum at ultricies vel, eleifend vitae sem. Aenean auctor euismod velit in tristique. Morbi vel odio ornare, fringilla nulla sit amet, porttitor neque. Morbi tristique iaculis nisi eget porttitor.\nMauris varius semper metus. Sed tempor commodo enim viverra posuere. Phasellus consectetur venenatis nisi, sed dictum libero fringilla sit amet. Etiam sed enim leo. Pellentesque pellentesque mauris augue, eleifend fringilla dui interdum vitae. Vestibulum lobortis sem efficitur viverra tempus. Nam quis aliquet velit. Nunc lobortis cursus ullamcorper. Suspendisse imperdiet elit sit amet dui condimentum porta. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.\nSed id fermentum mi. Proin sit amet est sed ante semper maximus.\nSed placerat ipsum a ipsum tristique laoreet in nec felis. Aenean ultrices, metus sed pellentesque egestas, tortor risus ullamcorper nisl, vitae sollicitudin risus libero et est. Morbi non elit porttitor, dapibus sem ac, elementum mi. Curabitur ut sodales nisl, a volutpat mauris. Ut eget diam justo. Quisque bibendum orci eget orci pharetra, ut consequat mauris dapibus. Quisque mauris nulla, aliquam at aliquam vitae, accumsan ac justo. Ut at mi dui. Nullam sem nisi, lacinia nec tincidunt in, tincidunt a dui. Nunc rutrum vestibulum cursus. Nam lobortis porta metus, sit amet ullamcorper ligula porta porttitor. Nulla eget condimentum ligula, quis maximus tortor. Nam vel hendrerit arcu.",
    };
  },
};
</script>
