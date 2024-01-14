<template>
  <h1>Reaction game</h1>
  <button ref="playButton" @keydown.space="start" :disabled="isPlaying">
    Play (by pressing space)
  </button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
  <div v-if="isPlaying" @click="showToerly" class="gray_block">Don't press</div>
  <h1>{{ message }}</h1>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      toErly: false,
      message: null,
    };
  },
  mounted() {
    this.$refs.playButton.focus();
  },
  updated() {
    this.$refs.playButton.focus();
  }, 
  methods: {
    start() {
      this.delay = 1000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
      this.message = null;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
    showToerly() {
      if (this.showToerly) {
        this.toErly = true;
        this.message =
          "You have to wait for the green field and only then click. Click Play and try again.";
        this.isPlaying = false;
      }
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
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}

.gray_block {
  width: 400px;
  border-radius: 20px;
  background: #4444;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
  font-weight: 600;
}
</style>
