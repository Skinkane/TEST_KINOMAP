<template>
  <div id="app">
    <img alt="Kinomap logo" src="./assets/logo.png">
    <Carrousel />
  </div>
</template>

<script>
import Carrousel from './components/Carrousel.vue'

export default {
  name: 'App',
  components: {
    Carrousel
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
