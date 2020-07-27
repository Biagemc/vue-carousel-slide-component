<template>
  <div id="app">
    <carousel @next="next" @prev="prev">
      <carousel-slide
        v-for="(slide, index) in slides"
        :key="slide"
        :index="index"
        :visibleSlide="visibleSlide"
        :flowDirection="flowDirection"
      >
        <img :src="slide" />
      </carousel-slide>
    </carousel>
  </div>
</template>

<script>
import Carousel from "./components/Carousel";
import CarouselSlide from "./components/CarouselSlide";

function getPreviousValidIndex(index, length) {
  const deprecatedIndex = index - 1;
  return deprecatedIndex < 0 ? length - 1 : deprecatedIndex;
}

function getNextValidIndex(index, length) {
  const incrementedIndex = index + 1;
  return incrementedIndex > length ? 0 : incrementedIndex;
}

export default {
  data() {
    return {
      slides: [
        "https://picsum.photos/id/237/600/350",
        "https://picsum.photos/id/236/600/350",
        "https://picsum.photos/id/235/600/350",
        "https://picsum.photos/id/234/600/350",
      ],
      visibleSlide: 0,
      flowDirection: "left",
    };
  },
  components: {
    Carousel,
    CarouselSlide,
  },
  computed: {
    slidesLen() {
      return this.slides.length;
    },
  },
  methods: {
    next() {
      if (this.visibleSlide >= this.slidesLen - 1) {
        this.visibleSlide = 0;
      } else {
        this.visibleSlide++;
      }
      this.flowDirection = "left";
    },
    prev() {
      if (this.visibleSlide <= 0) {
        this.visibleSlide = this.slidesLen - 1;
      } else {
        this.visibleSlide--;
      }
      this.flowDirection = "right";
    },
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
}
</style>
