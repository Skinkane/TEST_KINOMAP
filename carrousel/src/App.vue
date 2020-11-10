<template>
  <div id='app'>
    <b-carousel ref="myCarousel" id="carousel-1" v-model="slide" :interval="4000" controls indicators background="#ababab" img-width="220" img-height="100" style="text-shadow: 1px 1px 2px #333;" @sliding-start="onSlideStart" @sliding-end="onSlideEnd">
      <b-carousel-slide img-src="http://62.210.247.201:9000/BTWIN.png"></b-carousel-slide>
      <b-carousel-slide img-src="http://62.210.247.201:9000/adidas.png"></b-carousel-slide>
      <b-carousel-slide img-src="http://62.210.247.201:9000/bhfitness.png"></b-carousel-slide>
      <b-carousel-slide img-src="http://62.210.247.201:9000/domyos.png"></b-carousel-slide>
    </b-carousel>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  components: {
  },
  data() {
      return {
        slide: 0,
        sliding: null
      }
    },
  methods: {
  },
  mounted () {
    axios
      .get('http://62.210.247.201:9000/test')
      .then(response => (this.images = response))
      .catch(error => {
        console.log(error)
        this.errored = true})
    }
}
</script>
<style>
  #app{
    width: 50%;
    display: center;
  }
</style>
