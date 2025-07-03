<template>
  <div class="container">
    <h2>🎓 학생 성적 보기</h2>
    <div class="score-box">
      <input
        type="number"
        v-model="score"
        placeholder="점수를 입력하세요 (0~100)"
      />
      <div class="grade-message">
        <p v-if="score >= 90" class="grade a">훌륭합니다! A 학점 🎉</p>
        <p v-else-if="score >= 80" class="grade b">잘했어요! B 학점 🙂</p>
        <p v-else-if="score >= 70" class="grade c">노력했어요! C 학점 😅</p>
        <p v-else class="grade d">다음엔 더 잘할 수 있어요! 💪</p>
      </div>
    </div>

    <hr />

    <h2>🍉 과일 리스트</h2>
    <ul class="fruit-list">
      <li v-for="(fruit, idx) in fruits" :key="idx">
        <span class="index">{{ idx + 1 }}.</span> {{ fruit }}
      </li>
    </ul>
    <p v-show="fruits.length === 0" class="empty">과일이 없습니다 🥺</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const score = ref(85);
const fruits = ref(["사과", "바나나", "포도", "오렌지"]);
</script>

<style scoped>
.container {
  max-width: 480px;
  margin: 40px auto;
  padding: 24px;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06);
  font-family: "Segoe UI", sans-serif;
}

h2 {
  margin-bottom: 12px;
  color: #333;
  font-weight: bold;
}

input {
  width: 100%;
  padding: 10px 12px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 8px;
  margin-bottom: 12px;
}

.score-box {
  margin-bottom: 20px;
}

.grade-message .grade {
  padding: 10px;
  border-radius: 8px;
  font-weight: bold;
  text-align: center;
}

.grade.a {
  background: #e0fbe0;
  color: #28a745;
}
.grade.b {
  background: #e8f5ff;
  color: #007bff;
}
.grade.c {
  background: #fff9e6;
  color: #ffc107;
}
.grade.f {
  background: #ffe8e8;
  color: #dc3545;
}

.fruit-list {
  list-style: none;
  padding-left: 0;
  margin: 0;
}

.fruit-list li {
  background: #f9f9f9;
  border: 1px solid #ddd;
  padding: 10px 12px;
  margin-bottom: 8px;
  border-radius: 6px;
  font-size: 15px;
  display: flex;
  align-items: center;
}

.index {
  display: inline-block;
  width: 24px;
  font-weight: bold;
  color: #42b983;
}

.empty {
  margin-top: 16px;
  text-align: center;
  color: #aaa;
  font-style: italic;
}
</style>
