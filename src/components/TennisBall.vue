<template>
  <h1 v-show="showBlock" @click="stopTimer">🥎</h1>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: 0,
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
    startTimer(this: { timer: number; reactionTime: number }) {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer(this: { timer: number; reactionTime: number }) {
      clearInterval(this.timer);
      alert(this.reactionTime);
    },
  },
});
</script>

<style scoped>
h1 {
  margin: 2rem;
  cursor: pointer;
}
</style>
