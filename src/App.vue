<template>
  <div id="app">
    <carousel>
      <carousel-slide
        v-for="(slide, index) in slides"
        :key="slide"
        :index="index"
        :visibleSlide="visibleSlide"
      >
        <img :src="slide" />
      </carousel-slide>
    </carousel>
  </div>
</template>

<script>
import Carousel from "./components/Carousel";
import CarouselSlide from "./components/CarouselSlide";
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
    };
  },
  components: {
    Carousel,
    CarouselSlide,
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
}
</style>
