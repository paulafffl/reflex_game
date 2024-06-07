<template>
  <h1 v-show="showBall" @click="stopTimer">🥎</h1>
  <div v-show="showLoading" class="loader"></div>
  <ResultsModal v-if="showModal" :score="reactionTime" @close="toggleModal" />
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
      showBall: false,
      timer: 0,
      reactionTime: 0,
      showLoading: false,
    };
  },
  mounted() {
    this.showLoading = true;
    setTimeout(() => {
      this.showLoading = false;
      this.showBall = true;
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
      this.showBall = false;
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

.loader {
  margin-top: 3rem;
  width: 60px;
  aspect-ratio: 2;
  --_g: no-repeat radial-gradient(circle closest-side, #fff 90%, #0000);
  background: var(--_g) 0% 50%, var(--_g) 50% 50%, var(--_g) 100% 50%;
  background-size: calc(100% / 3) 50%;
  animation: dots 1s infinite linear;
}
@keyframes dots {
  20% {
    background-position: 0% 0%, 50% 50%, 100% 50%;
  }
  40% {
    background-position: 0% 100%, 50% 0%, 100% 50%;
  }
  60% {
    background-position: 0% 50%, 50% 100%, 100% 0%;
  }
  80% {
    background-position: 0% 50%, 50% 50%, 100% 100%;
  }
}
</style>
