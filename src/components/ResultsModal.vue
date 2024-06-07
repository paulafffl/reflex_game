<template>
  <div class="backdrop" @click="closeModal">
    <div class="modal">
      <h2>YOUR TIME:</h2>
      <h1>{{ score }}ms</h1>
      <p>
        That's a <strong>{{ rank }}</strong> reflex
      </p>
      <p class="info">(click anywhere to restart)</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "⚡Lightning";
    }
    if (this.score < 400) {
      this.rank = "🚀Quick";
    } else {
      this.rank = "🐢Slow";
    }
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.modal {
  width: auto;
  height: auto;
  padding: 40px;
  padding-bottom: 50px;
  background: white;
  border-radius: 4px;
  border: 8px solid black;
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
.info {
  font-size: 0.8rem;
  margin-top: 1rem;
}
h1,
h2,
p {
  margin: 00;
  color: black;
}
</style>
