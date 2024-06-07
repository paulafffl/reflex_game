<template>
  <h1>🎾 Reflex&nbsp;Game</h1>
  <h2>How fast are your reflexes? Find&nbsp;out&nbsp;now!</h2>
  <TennisCourt />
  <button v-if="!hasPlayed" @click="start">PLAY</button>
  <TennisBall v-if="isPlaying" :delay="delay" @restart="restart" />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import TennisBall from "./components/TennisBall.vue";
import TennisCourt from "./components/TennisCourt.vue";

@Options({
  components: {
    TennisBall,
    TennisCourt,
  },
})
export default class App extends Vue {
  isPlaying = false;
  hasPlayed = false;
  delay = 0;
  start() {
    this.delay = 1000 + Math.random() * 5000;
    this.hasPlayed = true;
    this.isPlaying = true;
  }
  restart() {
    this.hasPlayed = false;
    this.isPlaying = false;
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: top;
  align-items: center;
  text-align: center;
  height: 100vh;
  width: 100%;
  @media (max-width: 767px) {
    justify-content: space-evenly;
  }
}
button {
  background: #4d8dd7;
  box-shadow: inset -0.3rem -0.3rem #084db2;
  color: white;
  border: none;
  padding: 16px 22px;
  padding-top: 14px;
  border-radius: 14px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 40px auto;
  font-size: 2rem;
}
button:hover {
  background: #084db2;
  transition: background-color 0.3s ease;
}
h1 {
  margin-bottom: 1rem;
}
</style>
