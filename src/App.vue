<template>
  <h1>Faster reactions</h1>
  <button type="button" @click="start" :disabled="isPlaying">start</button>

  <Block v-if="isPlaying" :delay="delay" @end='endGame'/>
  <Results v-if="showResult" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay:null,
      score:null,
      showResult: false
    }
  },
  components: { Block, Results },
  methods: {
    start(){
      this.delay = 2000 + Math.random()* 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  },
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

button{
  background-color: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 1rem;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled]{
  opacity: 0.4;
  cursor: not-allowed;
}

</style>
