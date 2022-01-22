<template>
  <h1>{{ title }}</h1>
  <button @click="start" :disabled="isPlaying">PLAY 🎲</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results :score="score" v-if="showResults" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      title: "Ninja Reaction Timer",
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start: function () {
      this.delay = 2000 + Math.random() * 4000;
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
  color: #444;
  margin-top: 60px;
}
#app h1 {
  width: 400px;
  margin: 0 auto 20px auto;
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
}
#app button {
  padding: 10px;
  background: #0faf87;
  color: white;
  border-radius: 8px;
  cursor: pointer;
  margin: 10px;
  letter-spacing: 1px;
  border: none;
}
#app button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
