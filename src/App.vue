<template>
  <div id="app">
    <h1>Reaction Timer Game</h1>
    <button @click="start">Fire Game</button>
    <BlockComp />
  </div>
</template>

<script>
import BlockComp from "./components/BlockComp.vue";
export default {
  name: "App",
  components: { BlockComp },
};
</script>

<script setup>
import { ref } from "vue";

const data = ref({
  isPlaying: false,
  delay: null,
});

function start() {
  data.value.delay = 2000 + Math.random() * 5000;
  data.value.isPlaying = true;
  console.log(data.value.delay);
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
