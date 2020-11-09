<template>
  <div>
    <carrousel>
      <carrousel-slide>
        <div id=app>
          <img src="http://62.210.247.201:9000/reebok.png">
        </div>
      </carrousel-slide>
      <carrousel-slide>
         <div id=app>
          <img src="http://62.210.247.201:9000/Hammer.png">
        </div>
      </carrousel-slide>
    </carrousel>
  </div>
</template>

<script>
import axios from 'axios'
import Carrousel from './components/Carrousel.vue'
import CarrouselSlide from './components/CarrouselSlide.vue'

export default {
  name: 'App',
  components: {
    Carrousel,
    CarrouselSlide
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
