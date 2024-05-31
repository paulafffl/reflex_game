<template>
  <div class="court">
    <p class="side">
      <strong>1.</strong> After you click PLAY, a tennis ball will eventually
      appear on the screen.
    </p>
    <p class="side">
      <strong>2.</strong> Click on it as quickly as you can and find out how
      fast your reflexes are!
    </p>
  </div>
</template>

<script>
export default {
  props: ["delay"],
};
</script>

<style scoped>
.court {
  display: flex;
  border: 2px solid white;
  @media (max-width: 767px) {
    flex-direction: column;
  }
}
.side {
  background: #1f4b42;
  width: 20vw;
  padding: 5rem 2.5rem;
  border: 2px solid white;
  margin: 0;
  @media (max-width: 767px) {
    padding: 2rem;
    padding-top: 1r.5em;
    width: 50vw;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
