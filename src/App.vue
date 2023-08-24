<template>
  <div>
    <h1>Check your reflexes</h1>
    <button @click="start" :disabled="isPlaying">PLAY</button>
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
*{
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #d8d8d8;
  background-color: #444;
  margin-top: 30px;
}

button {
  background: #159251;
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