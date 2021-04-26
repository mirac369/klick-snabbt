<template>
 <h1>Reaktionstid</h1>
 <button @click="start" :disabled="isPlaying">Play</button>
 <Blokering v-if="isPlaying" v-bind:delay="delay" @slut="slutSpel" />
 <Resultat v-if="showResults" :score="score" />
</template>

<script>
import Blokering from './components/Blokering.vue'
import Resultat from './components/Resultat.vue'

export default {
  name: 'App',
  components: {Blokering, Resultat},
  data() {
    return{
     isPlaying: false,
     delay: null,
     score: null,
     showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 3000 + Math.random() * 6000
      this.isPlaying = true
      this.showResults = false
    },
    slutSpel(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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
button{
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
opacity: 0.2;
cursor: not-allowed;
}
</style>
