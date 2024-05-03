<script setup>
import { ref } from "vue";
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

const isPlaying = ref(false);
const delay = ref(null);
const score = ref(null);
const start = () => {
  delay.value = 2000 + Math.random() * 5000;
  isPlaying.value = true;
};
const endGame = (reactionTime) => {
  score.value = reactionTime;
  isPlaying.value = false;
};
</script>

<template>
  <div class="container">
    <div class="header">
      <h1>Reaction Timer</h1>
      <button @click="start" :disabled="isPlaying">play</button>
      <Results :score="score" />
    </div>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.header {
  position: fixed;
  top: 0;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
