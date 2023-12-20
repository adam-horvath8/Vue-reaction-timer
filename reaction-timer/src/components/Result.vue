<template>
  <div>
    <p>Your Score: {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";

let rank = ref(null);

let { score } = defineProps(["score"]);

onMounted(() => {
  if (score < 250) {
    rank.value = "Ninja Fingers";
  } else if (score < 400) {
    rank.value = "Rapid Reflexes";
  } else {
    rank.value = "Snail pace...";
  }
});
</script>

<style>
.rank {
  font-size: 1.4rem;
  color: #2a5adb;
  font-weight: bold;
}
</style>
