<template>
  <h1 v-show="showBlock" @click="stopTimer">🥎</h1>
  <ResultsModal
    v-if="showModal"
    heading="Your time was"
    :text="reactionTime"
    @close="toggleModal"
  />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ResultsModal from "./ResultsModal.vue";

export default defineComponent({
  props: ["delay", "hasPlayed", "isPlaying"],
  components: { ResultsModal },
  restart: ["close"],
  data() {
    return {
      showModal: false,
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
    toggleModal(): void {
      this.showModal = !this.showModal;
      this.timer = 0;
      this.reactionTime = 0;
      this.$emit("restart");
    },
    startTimer(): void {
      this.timer = window.setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer(): void {
      clearInterval(this.timer);
      this.showBlock = false;
      this.showModal = true;
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
