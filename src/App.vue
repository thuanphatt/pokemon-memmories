<template>
  <div>
    <main-screen
      v-if="statusMatch === 'default'"
      @onStart="onHandleBeforeStart($event)"
    />
    <interact-screen
      v-if="statusMatch === 'match'"
      :cardsContext="settings.cardsContext"
    />
    <copy-right-screen />
  </div>
</template>

<script>
import MainScreen from './components/MainScreen.vue'
import InteractScreen from './components/InteractScreen.vue'
import CopyRightScreen from './components/CopyRightScreen.vue'
import { shuffed } from './utils/array'
export default {
  name: 'App',
  data() {
    return {
      settings: {
        totalOfBlocks: 0,
        cardsContext: [],
        startedAt: null,
      },
      statusMatch: 'default',
    }
  },

  components: {
    CopyRightScreen,
    MainScreen,
    InteractScreen,
  },
  methods: {
    onHandleBeforeStart(config) {
      this.settings.totalOfBlocks = config.totalOfBlocks
      const fisrtCard = Array.from(
        { length: this.settings.totalOfBlocks / 2 },
        (_, i) => i + 1
      )
      const secondCards = [...fisrtCard]
      const cards = [...fisrtCard, ...secondCards]
      this.settings.cardsContext = shuffed(shuffed(shuffed(cards)))
      this.settings.startedAt = new Date().getTime()

      // data ready
      this.statusMatch = 'match'
    },
  },
}
</script>
