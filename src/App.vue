<template>
  <h1>🎾 Reflex&nbsp;Game</h1>
  <h2>How fast are your reflexes? Find&nbsp;out&nbsp;now!</h2>
  <TennisCourt />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import TennisCourt from "./components/TennisCourt.vue";

@Options({
  components: {
    TennisCourt,
  },
})
export default class App extends Vue {}
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
h1 {
  margin-bottom: 1rem;
}
</style>
