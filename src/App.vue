<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play Game</button>
  <Block @reactTime="logTime" v-if="isPlaying" :delay="delay" />
  <Results v-if="showResults" :playing="isPlaying" :score="score" />
</template>

<script>
import Block from "./components/Block";
import Results from "./components/Results";

export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  components: {
    Block,
    Results,
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    logTime(data) {
      this.score = data;
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
  color: #444;
  margin-top: 60px;
}
</style>
