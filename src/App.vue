<template>
  <h1>Ninja Reaction Timer</h1>
  <button  @click="start" :disabled="isPlaying">Play</button>
  <BlockItem v-if="isPlaying" :delay="delay" @score="endGame" />
  <Results v-if="showResults" :score ="score"/>
</template>

<script >
import BlockItem from './components/BlockItem.vue';
import Results from './components/Results.vue';
export default {
  components:{
    BlockItem,
    Results
  },
  data(){
    return {
      isPlaying: false,
      delay:null,
      score : null,
      showResults : false,
    }
  },
  
  
  methods :{
    start(){
      this.delay = 2000 + Math.random() *5000;
      this.isPlaying = true;
      this.showResults = false;
      
      
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    }
  }
  
  
}

</script>


<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
