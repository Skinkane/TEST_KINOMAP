<template>
  <div id="app">
    <img alt="Kinomap logo" src="./assets/logo.png">
    <carrousel>
      <carrousel-slide>
        <img src="http://62.210.247.201:9000/reebok.png">
      </carrousel-slide>
      <carrousel-slide>
         <img src="http://62.210.247.201:9000/Hammer.png">
      </carrousel-slide>
    </carrousel>
  </div>
</template>

<script>
import Carrousel from './components/Carrousel.vue'
import CarrouselSlide from './components/CarrouselSlide.vue'

export default {
  name: 'App',
  components: {
    Carrousel,
    CarrouselSlide
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
