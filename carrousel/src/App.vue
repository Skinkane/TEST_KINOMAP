<template>
  <div id='app'>
    <div class="d-flex justify-content-center">
      <img src="./assets/logo.png">
    </div>
    <div>
      {{images}}
    </div>
    <b-carousel class="justify-content-center w-25 p-3 d-flex" ref="myCarousel" id="carousel-1" v-model="slide" :interval="2000" controls indicators background="#fff" img-width="1024" img-height="1024" style="text-shadow: 1px 1px 2px #333;">
      <div  v-for="image in images" :key="image.image">
        <b-carousel-slide class="zoom" v-bind:img-src="image.image"></b-carousel-slide>
      </div>
    </b-carousel>
    <p class="d-flex justify-content-center">Par Gautier Couture</p>
  </div>
</template>

<script>
import axios from 'axios'
import shuffle from 'lodash/shuffle'

export default {
  name: 'App',
  created() {
    this.getApi();
  },
  data: function() {
      return {
        images: [],
        slide: 0,
        sliding: null
      }
    },
    methods: {
      getApi() { 
        axios.get('http://62.210.247.201:9000/test').then(response => (this.images = response.data)).catch(error => {console.log(error)});
        for(var i = 0; i < 13; i++){
          for(var j = 0; j < this.images[i].weight; j++){
            this.images.push(this.images[i])
          }
        }
        shuffle(this.images)
      }
    }
}
</script>
<style>
#app{
  background-color: rgb(241, 214, 0);
}

.zoom {
  transition: transform .2s;
  margin: 0 auto;
}

.zoom:hover {
  transform: scale(1.5); 
}
</style>
