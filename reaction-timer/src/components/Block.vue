<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script setup>
import { onMounted, ref } from "vue";

let showBlock = ref(false);
let timer = null;
let reactionTime = 0;

const { delay } = defineProps(["delay"]);

const emit = defineEmits(["end"]);

const startTimer = () => {
  timer = setInterval(() => {
    reactionTime += 10;
  }, 10);
};

const stopTimer = () => {
  clearInterval(timer);
  emit("end", reactionTime);
};

onMounted(() => {
  setTimeout(() => {
    showBlock.value = true;
    startTimer();
  }, delay);
});
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
