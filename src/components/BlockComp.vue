<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
  props: ['delay'],
  data(){
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    }
  },
  mounted(){
    console.log("the Component is mounted"),
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
      console.log(this.delay)
    }, this.delay)
  },
  methods: {
    startTimer(){
      this.timer = setInterval(() => {
        this.reactionTime += 8
      }, 8)
    },
    stopTimer(){
      clearInterval(this.timer)
      console.log(this.reactionTime)
      this.$emit('end', this.reactionTime)
    }
  }
}
</script>

<style>
  .block {
    width: 400px;
    border-radius: 20px;
    background:  rgb(16, 123, 59);;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>