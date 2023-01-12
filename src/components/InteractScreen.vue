<template lang="">
  <div>
    <h1>This is a Interact Screen</h1>
    <card-flip
      v-for="(card, index) in cardsContext"
      :key="index"
      :ref="`card-${index}`"
      :imgBackFaceUrl="`images/${card}.png`"
      :card="{ index, value: card }"
      :rules="rules"
      @onFlip="checkRule($event)"
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
  data() {
    return {
      rules: [],
    }
  },
  methods: {
    checkRule(card) {
      if (this.rules.length === 2) return false
      this.rules.push(card)
      if (
        this.rules.length === 2 &&
        this.rules[0].value === this.rules[1].value
      ) {
        console.log('Right...')
        this.$refs[`card-${this.rules[0][0].index}`].onEnabledDisabledMode()
        this.$refs[`card-${this.rules[1][0].index}`].onEnabledDisabledMode()
        this.rules = []
      } else if (
        this.rules.length === 2 &&
        this.rules[0].value !== this.rules[1].value
      ) {
        console.log('wrong!')
        setTimeout(() => {
          this.$refs[`card-${this.rules[0].index}`][0].onFlipBackCard()
          this.$refs[`card-${this.rules[1].index}`][0].onFlipBackCard()
          this.rules = []
        }, 800)
      } else return false
    },
  },
}
</script>
