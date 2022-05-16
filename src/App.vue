<template>
    <h1>  MPT reaction timer </h1>
    <button @click="start" :disabled="isPlaying">Start</button>

     <Block v-if="isPlaying" :delay="delay" @end="endGame"/>

     <Results v-if="showResults" :score="score"  />

</template>


<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: "App",
  data() {
    return{
      isPlaying: false,
      showResults: false,
      delay: null,
      score: null,
    }
  },
  components: {
    Block, Results
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}

</script>


<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  color: #FCEDDA;
  font-weight: normal;
  text-align: center;
  
}

#app h1 {
  font-size: 7rem;
  font-weight: 700;
  animation: 1s ease-out 0s 1 slideInFromTop;
}

button {

  background: #201E21 ;
  color:  #FCEDDA;
  border: none;
  border-radius: 4px;
  font-size: 2rem;
  letter-spacing: 2px;
  padding: 10px;
  cursor: pointer;
  margin: 10px;
  font-weight: bold;
}
button:hover {
  background: #FCEDDA;
  color: #201E21;

}

button[disabled] {
  background: #201E21 ;
  color:  #FCEDDA;
  opacity: 0.4;
  cursor: not-allowed;
  
}

@media screen and (max-width: 405px){
   html {
     font-size: 40%;
   }
}
</style>
