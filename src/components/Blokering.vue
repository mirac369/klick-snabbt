<template>
  <div class="blokering" v-if="showBlokering" @click="stopTimer">
      klicka mig
  </div>
  
</template>

<script>
export default {
props: ['delay'],
data() {
return {
  showBlokering: false,
  timer: null,
  reactionTime: 0
}
},
mounted() {
  setTimeout(() => {
    this.showBlokering = true
    this.startTimer()
  }, this.delay)
},
methods: {
  startTimer() {
    this.timer = setInterval(() => {
      this.reactionTime += 11
    }, 11)
  },
  stopTimer() {
    clearInterval(this.timer)
    this.$emit('slut', this.reactionTime)
  }
}
}
</script>

<style>
.blokering{
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0px;
    margin: 40px auto;
}
</style>