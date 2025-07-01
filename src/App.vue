<script setup>
import {ref} from 'vue'

const message = ref('안녕하세요, Vue 3!')
</script>

<template>
  <div>
    <h1>{{ message }}</h1>
    <p>Vue 3 튜토리얼에 오신 것을 환영합니다!</p>
  </div>
</template>

<style scoped>
  h1 {
    color: #42b983;
  }
</style>
