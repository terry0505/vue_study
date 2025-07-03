<template>
  <div>
    <h2>카운터 앱</h2>
    <p>현재 값: {{ count }}</p>
    <button @click="decrease">-1</button>
    <button @click="increase">+1</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const count = ref(0);

function increase() {
  count.value++;
}

function decrease() {
  count.value--;
}
</script>

<style scoped>
button {
  margin: 4px;
  padding: 6px 10px;
  font-weight: bold;
}
</style>
