<template>
  <div id="app">
    <h1>Reaction Timer Game</h1>
    <button @click="start">Fire Game</button>
  </div>
</template>
<script>
export default {
  name: "App",
  components: {},
};
</script>

<script setup>
import { ref } from "vue";

const data = ref({
  isPlaying: false,
  delay: null,
});

function start() {
  data.delay.value = 2000 + Math.random() * 5000;
  data.isPlaying.value = true;
  console.log(data.delay.value);
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
