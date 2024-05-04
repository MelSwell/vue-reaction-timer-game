<template>
  <p>{{ finalMessage }}</p>
</template>

<script>
export default {
  props: ['resultTime'],
  data() {
    return {
      finalMessage: null
    }
  },
  mounted() {
    this.setFinalMessage(this.resultTime)
  },
  methods: {
    setFinalMessage(resultTime) {
      const resultString = resultTime.toFixed(2)
      if (resultTime <= 0.3) {
        this.finalMessage = `Woah, slow down there, Clint Eastwood! That was ${resultString}s! Any faster than that and you'll break the program!`
      } else if (resultTime > 0.3 && resultTime <= 0.5) {
        this.finalMessage = `Hey, you're pretty good at this! That was ${resultString}s!`
      } else if (resultTime > 0.5 && resultTime <= 1) {
        this.finalMessage = `${resultString}s... Not bad, but I think you can do better!`
      } else if (resultTime > 1 && resultTime <= 4) {
        this.finalMessage = `${resultString}s... Stop looking at your phone!` 
      } else {
        this.finalMessage = `${resultString}s... Are you even there?` 
      }
    }
  }
}
</script>

<style>

</style>