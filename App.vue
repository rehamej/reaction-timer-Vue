<template>
<h1> reaction-timer </h1>
<button @click="start" :disabled="isPlaying" >paly</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<!-- <p v-if="showResults">reaction time : {{ score }} ms</p> -->
<Results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score : null,
      showResults : false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000 //a random amount in miliseconds between 0 amd 5000 miliseconds
      this.isPlaying = true
      console.log(this.delay)
      this.showResults= false
    },

  endGame(reactionTimer){
    this.score = reactionTimer
    this.isPlaying= false
    this.showResults= true
  },

  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
