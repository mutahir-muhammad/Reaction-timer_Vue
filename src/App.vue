<template>
  <div>
    <h1>Ninja Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">play</button>
    <BlockComp v-if="isPlaying" :delay="delay" @end="end" />
    <ResultsComp v-if="showResult" :score="score" />
  </div>
</template>

<script>
import BlockComp from './components/BlockComp.vue'
import ResultsComp from './components/ResultsComp.vue'

export default {
  name: 'App',
  components: { BlockComp, ResultsComp },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    }
  },
  methods: {
    start() {
      // set time amount (ms)
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    end(result){
      this.score = result
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
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

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>