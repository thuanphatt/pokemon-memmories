<template>
  <div>
    <main-screen
      v-if="statusMatch === 'default'"
      @onStart="onHandleBeforeStart($event)"
    />
    <interact-screen v-if="statusMatch === 'match'" />
    <copy-right-screen />
  </div>
</template>

<script>
import MainScreen from "./components/MainScreen.vue";
import InteractScreen from "./components/InteractScreen.vue";
import CopyRightScreen from "./components/CopyRightScreen.vue";
export default {
  name: "App",
  data() {
    return {
      statusMatch: "default",
    };
  },

  components: {
    CopyRightScreen,
    MainScreen,
    InteractScreen,
  },
  methods: {
    onHandleBeforeStart(config) {
      console.log("running hanle before start", config);
      this.statusMatch = "match";
    },
  },
};
</script>
