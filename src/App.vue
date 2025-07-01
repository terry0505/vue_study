<template>
  <div>
    <h2>이름을 입력해보세요.</h2>
    <input v-model="name" placeholder="이름 입력" />
    <p>안녕하세요, {{ name }}님!</p>

    <h2>reactive 객체 실습</h2>
    <input v-model="user.firstName" placeholder="이름 입력" />
    <input v-model="user.lastName" placeholder="성 입력" />
    <p>안녕하세요, {{ user.firstName }} {{ user.lastName }}님!</p>
  </div>
</template>

<script setup>
import { reactive, ref } from "vue";

const name = ref("홍길동"); //단일 값
const user = reactive({
  firstName: "홍",
  lastName: "길동"
}); //객체
</script>

<style scoped>
input {
  margin: 4px;
  padding: 4px;
}
</style>
