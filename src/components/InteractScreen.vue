<template lang="">
  <div>
    <h1>This is a Interact Screen</h1>
    <card-flip
      v-for="(card, index) in cardsContext"
      :key="index"
      :imgBackFaceUrl="`images/${card}.png`"
    />
  </div>
</template>
<script>
import CardFlip from './CardPoke.vue'
export default {
  props: {
    cardsContext: {
      type: Array,
      default: function () {
        return []
      },
    },
  },
  components: {
    CardFlip,
  },
}
</script>
