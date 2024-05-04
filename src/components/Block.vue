<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    CLICK ME FAST!
  </div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    }, 
    stopTimer() {
      clearInterval(this.timer)
      this.showBlock = false
      this.$emit('endGame', (this.reactionTime * 0.001))
    }
  }
}
</script>

<style>
  .block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    font-size: x-large;
    text-align: center;
    padding: 90px 0px;
    margin: 40px auto;
  }
</style>