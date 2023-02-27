<template>
  <div>
    <h1> Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying" >Play</button>
    <Block v-if="isPlaying"  :delay="delay" @end="endGame" />
    <h1 v-if="showResults">Reaction Time Score :{{ score }}</h1>
  </div>
</template>

<script>
import Block from './components/Block.vue';
export default {
  name: 'App',
  components: { 
    Block,
  },
  data(){
    return {
      isPlaying:false,
      delay:null,
      score:0,
      showResults:false,
    }
  },
  methods:{
    start(){ 
      this.delay =  2000 + Math.random()*5000;
      console.log(this.delay);
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.showResults = true;
      this.isPlaying = false;
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
  color: #444;
  margin-top: 60px;
}
</style>
