<template>
    <div class="carousel">
        <slot></slot>
        <button class="carrousel_nav carrousel_prev" @click.prevent="prev"></button>
        <button class="carrousel_nav carrousel_next" @click.prevent="next"></button>
    </div>
</template>

<script>

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
.carrousel {
  position: relative;
}

.carrousel_nav {
  position : absolute;
  top : 50%;
  left: 10px;
  background: url(../assets/prev.png);
  width: 60px;
  height: 60px;
}

.carrousel_nav.carrousel_next{
  right: 10px;
  left: auto;
  background-image: url(../assets/next.png)
}
</style>