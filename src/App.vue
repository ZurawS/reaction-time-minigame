<template>
  <h1>Reaction Timer</h1>
  <h3>Check your reaction time!</h3>
  <button @click="start" :disabled="isPlaying">PLAY</button>
  <BlockComponent v-if="isPlaying" :delay="delay" @end="endGame" />
  <ResultsComponent v-if="showResults" :score="score" />
</template>

<script>
import BlockComponent from "./components/BlockComponent.vue";
import ResultsComponent from "./components/ResultsComponent.vue";

export default {
  name: "App",
  components: { BlockComponent, ResultsComponent },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 1000 + Math.random() * 3000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #194878;
  margin-top: 60px;
}
button {
  background: #0faf87;
  color: #fff;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
