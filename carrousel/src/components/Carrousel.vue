<template>
    <div class="carousel">
        <slot></slot>
        <button class="carrousel_nav carrousel_prev" @click.prevent="prev"></button>
        <button class="carrousel_nav carrousel_next" @click.prevent="next"></button>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Carrousel',
  data () {
    console.log(this.$children)
    return {
        index: 0,
        slides: []
    }   
  },
  mounted () {
    axios
      .get('http://62.210.247.201:9000/test')
      .then(response => (this.images = response))
      .catch(error => {
        console.log(error)
        this.errored = true})
    this.slides = this.$children
    this.slides.forEach((slide, i) => {
      slide.index = i
    })
  },

  computed: {
    slidesCount () { return this.slides.length}
  },

  methods: {
    next (){
      this.index++
      if(this.index >= this.slidesCount) {
        this.index = 0
      }
    },
    prev (){
      this.index--
      if(this.index < 0) {
        this.index  = this.slidesCount - 1
      }
    }
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

.carrousel {
  position: relative;
}

.carrousel_nav {
  position : absolute;
  top : 50%;
  left: 10px;
  background: url(../assets/prev.png);
  width: 312px;
  height: 312px;
}

.carrousel_nav.carrousel_next{
  right: 10px;
  left: auto;
  background-image: url(../assets/next.png)
}
</style>