<template>
    <div class="carousel">
        <div>
            <carousel :data="data" :indicators="false"></carousel>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Carrousel',
  components: {
  }, 
   data: () => {
    return {
        data: [
          '<div class="example-slide">Slide 1</div>',
          '<div class="example-slide">Slide 2</div>',
          '<div class="example-slide">Slide 3</div>',
        ],
        images : null,
        imageIndex: 0
    }
  },
  mounted () {
    axios
      .get('http://62.210.247.201:9000/test')
      .then(response => (this.images = response))
      .catch(error => {
        console.log(error)
        this.errored = true})
  },
  methods: {
    getImage(name){
        this.image = 'http://62.210.247.201:9000/'+name+'.png'
    },
    getNextImage(){
        if(this.imageIndex > this.list.length){
            this.imageIndex = 0;
        }
        else{
            this.imageIndex ++;
        }
    },
    getPreviewImage(){
        if(this.imageIndex < 0){
            this.imageIndex = this.list.length;
        }
        else{
            this.imageIndex --;
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
</style>