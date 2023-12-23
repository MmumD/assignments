<template>
  <div class="app">
    <carousel v-bind:items="carouselItems">
    </carousel>
  </div>
</template>

<script>
import Carousel from './components/Carousel.vue';

export default {
  data() {
    return {
      carouselItems: [ 
        {src: require('./assets/image1.jpeg'), alt:"Image 1", caption: 'Caption for Image 1'},
        {src: require('./assets/image2.jpeg'), alt:"Image 2", caption: 'Caption for Image 2'},
        {src: require('./assets/image3.jpeg'), alt:"Image 3", caption: 'Caption for Image 3'},
        {src: require('./assets/image4.jpeg'), alt:"Image 4", caption: 'Caption for Image 4'},
        {src: require('./assets/image5.jpeg'), alt:"Image 5", caption: 'Caption for Image 5'},
        {src: require('./assets/image6.jpeg'), alt:"Image 6", caption: 'Caption for Image 6'},
        {src: require('./assets/image7.jpeg'), alt:"Image 7", caption: 'Caption for Image 7'},
        {src: require('./assets/image8.jpeg'), alt:"Image 8", caption: 'Caption for Image 8'},
        {src: require('./assets/image9.jpeg'), alt:"Image 9", caption: 'Caption for Image 9'},
        {src: require('./assets/image10.jpeg'), alt:"Image 10", caption: 'Caption for Image 10'}
      ]
    };
  },
  components: {
    Carousel
  }
};
</script>
