<template>
  <div>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResults" :score="score" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

let isPlaying = ref(false);
let delay = null;
let score = ref(null);
let showResults = ref(false);

const start = () => {
  delay = 2000 + Math.random() * 5000;
  isPlaying.value = true;
  showResults.value = false;
};

const endGame = (reactionTime) => {
  score.value = reactionTime;
  isPlaying.value = false;
  showResults.value = true;
};
</script>

<style>
div {
  display: flex;
  flex-direction: column;
  align-items: center;
}

button {
  background: #2a5adb;
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
</style>
