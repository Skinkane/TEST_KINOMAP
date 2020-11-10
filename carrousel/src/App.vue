<template>
  <div id='app' class="container-fluid">
    <div class="row justify-content-center top-buffer">
      <img src="./assets/logo.png">
    </div>
    <div class="row justify-content-center top-buffer">
      <b-carousel ref="myCarousel" id="carousel-1" v-model="slide" :interval="2000" controls indicators background="#fff" style="text-shadow: 1px 1px 2px #333;">
        <div  v-for="image in images" :key="image.image">
          <b-carousel-slide class="zoom max" v-bind:img-src="image.image"></b-carousel-slide>
        </div>
      </b-carousel>
    </div>
    <div class="row justify-content-center top-buffer">
      <p>Par Gautier Couture</p>
    </div>
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
        src: [],
        slide: 0,
        sliding: null
      }
    },
    methods: {
      getApi() { 
        axios.get('http://62.210.247.201:9000/test').then(response =>{
          this.images = response.data
          for(var i = 0; i < 13; i++){
            for(var j = 0; j < this.images[i].weight -1; j++){
              this.images.push(this.images[i])
              this.images = shuffle(this.images)
            }
          }
        }).catch(error => {console.log(error)})
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

.top-buffer { 
 padding-top:30px; 
}

.max {
  width: auto;
  height: 150px;
}
</style>
