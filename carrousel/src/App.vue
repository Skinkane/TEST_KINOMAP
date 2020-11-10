<template>
  <div id='app'>
    <div class="d-flex justify-content-center">
      <img src="./assets/logo.png">
    </div>
    <b-carousel class="justify-content-center w-25 p-3 d-flex" ref="myCarousel" id="carousel-1" v-model="slide" :interval="4000" controls indicators background="#fff" img-width="1024" img-height="480" style="text-shadow: 1px 1px 2px #333;">
      <div  v-for="image in images" :key="image.image">
        <b-carousel-slide v-bind:img-src="image.image"></b-carousel-slide>
      </div>
    </b-carousel>
     <b-carousel-slide
        caption="First slide"
        text="Nulla vitae elit libero, a pharetra augue mollis interdum."
        img-src="http://62.210.247.201:9000/bhfitness.png"
      ></b-carousel-slide>

      <!-- Slides with custom text -->
      <b-carousel-slide img-src="http://62.210.247.201:9000/bhfitness.png">
        <h1>Hello world!</h1>
      </b-carousel-slide>
    <p class="d-flex justify-content-center">Par Gautier Couture</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  components: {
  },
  data: function() {
      return {
         images: [],
        slide: 0,
        sliding: null
      }
    },
  methods: {
  },
  mounted () {
    axios
      .get('http://62.210.247.201:9000/test')
      .then(response => (this.images = response.data))
      .catch(error => {
        console.log(error)
        this.errored = true})
    }
}
</script>
<style>
#app{
  background-color: rgb(241, 214, 0);
}

b-carousel-slide:hover{
  background-color: rgb(241, 214, 0);
}
</style>
