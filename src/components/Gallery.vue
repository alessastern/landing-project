<template>
  <div class="carousel">
    <div class="carousel-inner">
      <gallery-indicators
        v-if="indicators"
        :total="slides.length"
        :current-index="currentSlide"
        @switch="switchSlide($event)"
      ></gallery-indicators>
      <GalleryItem
        v-for="(slide, index) in slides"
        :slide="slide"
        :key="`item-${index}`"
        :current-slide="currentSlide"
        :index="index"
        :direction="direction"
        @mouseenter="stopSliderTimer"
        @mouseout="startSliderTimer"
      />
      <GalleryControls @prev="prev" @next="next" v-if="controls" />
    </div>
  </div>
</template>

<script>
import GalleryItem from "./GalleryItem.vue";
import GalleryControls from "./GalleryControls.vue";
import GalleryIndicators from "./GalleryIndicators.vue";
export default {
  props: {
    slides: {
      type: Array,
      required: true,
    },
    controls: {
      type: Boolean,
      default: false,
    },
    indicators: {
      type: Boolean,
      default: false,
    },
    interval: {
      type: Number,
      default: 5000,
    },
  },
  components: {
    GalleryItem,
    GalleryControls,
    GalleryIndicators,
  },
  data() {
    return {
      currentSlide: 0,
      slideInterval: 0,
      direction: "right",
    };
  },
  methods: {
    setCurrentSlide(index) {
      this.currentSlide = index;
    },
    prev(step = -1) {
      const index =
        this.currentSlide > 0
          ? this.currentSlide + step
          : this.slides.length - 1;
      this.setCurrentSlide(index);
      this.direction = "left";
      this.startSliderTimer();
    },
    _next(step = 1) {
      const index =
        this.currentSlide < this.slides.length - 1
          ? this.currentSlide + step
          : 0;
      this.setCurrentSlide(index);
      this.direction = "right";
    },
    next(step = 1) {
      this._next(step);
      this.startSliderTimer();
    },
    startSliderTimer() {
      this.stopSliderTimer();
      this.slideInterval = setInterval(() => {
        this._next();
      }, this.interval);
    },
    stopSliderTimer() {
      clearInterval(this.slideInterval);
    },
    switchSlide(index) {
      const step = index - this.currentSlide;
      step > 0 ? this.next(step) : this.prev(step);
    },
  },
  mounted() {
    this.startSliderTimer();
  },
  beforeUnmount() {
    this.stopSliderTimer();
  },
};
</script>

<style scoped>
.carousel {
  margin-top: 2em;
  display: flex;
  justify-content: center;
}

.carousel-inner {
  position: relative;
  width: 900px;
  height: 400px;
  overflow: hidden;
}
</style>
