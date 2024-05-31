<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <div v-if="showModal">
    <AppModal :heading="heading" :text="text" @close="toggleModal" />
  </div>
  <button @click="toggleModal">open modal</button>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import AppModal from "./components/AppModal.vue";

@Options({
  components: {
    AppModal,
  },
})
export default class App extends Vue {
  title = "My First Vue App!";
  heading = "Heading";
  text = "More info";
  showModal = false;
  toggleModal() {
    this.showModal = !this.showModal;
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
