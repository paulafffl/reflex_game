<template>
  <h1 v-show="showBlock" @click="stopTimer">🥎</h1>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.time = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      alert(this.reactionTime);
    },
  },
};
</script>

<style scoped>
h1 {
  margin: 2rem;
  cursor: pointer;
}
</style>
