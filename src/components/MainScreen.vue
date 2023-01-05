<template lang="">
  <div class="screen">
    <h1>POKE MEMORIES</h1>
    <h3>Select mode to start game</h3>
    <div class="actions">
      <button @click="onStart(16)">4x4</button>
      <span>Easy</span>
      <button @click="onStart(32)">6x6</button>
      <span>Normal</span>
      <button @click="onStart(64)">8x8</button>
      <span>Hard</span>
      <button @click="onStart(100)">10x10</button>
      <span>Super Hard</span>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    onStart(totalOfBlock) {
      this.$emit("onStart", { totalOfBlock });
    },
  },
};
</script>
<style lang=""></style>
