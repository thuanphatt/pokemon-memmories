<template lang="">
  <div class="card">
    <div class="card__inner">
      <div class="card__face card__face--front">
        <div class="card__content">Front</div>
      </div>
      <div class="card__face card__face--back">
        <div class="card__content">Back</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {};
</script>
<style lang="css" scoped>
.card {
  display: inline-block;
  margin-right: 1rem;
  margin-bottom: 1rem;
  width: 90rem;
  height: 120rem;
}
.card__inner {
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
}
.card__inner.is-flipped {
  transform: rotateY(-180deg);
}
.card__face {
  position: absolute;
}
</style>
