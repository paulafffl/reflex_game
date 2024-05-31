<template>
  <div class="backdrop" @click="closeModal">
    <div class="modal" :class="{ alert: theme === 'alert' }">
      <h2>{{ heading }}</h2>
      <h1>{{ text }}</h1>
      <p>(click anywhere to play again)</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["heading", "text", "theme"],
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.modal {
  width: 400px;
  height: auto;
  padding: 40px;
  padding-bottom: 50px;
  background: #4d8dd7;
  border-radius: 10px;
}
.backdrop {
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.modal.alert {
  background: crimson;
}
h1,
h2,
p {
  margin: 0;
}
</style>
