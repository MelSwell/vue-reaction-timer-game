<template>
  <h1>Reaction Timer</h1>
  <button :disabled="isPlaying" @click="start">play</button> 
  <Block v-if="isPlaying" :delay="delay" @endGame="endGame" />
  <Results v-if="showResults" :resultTime="resultTime" />
</template>

<script>
  import Block from "./components/Block.vue";
  import Results from "./components/Results.vue";
  export default {
    name: 'App',
    components: { Block, Results },
    data() {
      return {
        isPlaying: false,
        delay: null,
        showResults: false,
        resultTime: null
      }
    },
    methods: {
      start() {
        this.delay = 2000 + Math.random() * 6000
        this.isPlaying = true
        this.showResults = false
      },
      endGame(result) {
        this.resultTime = result
        this.showResults = true
        this.delay = null
        this.isPlaying = false
      }
    }
  }
</script>


<style>

</style>
