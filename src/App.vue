<template>
  <div class="container">
    <h2>📝 나만의 메모장</h2>

    <div class="input-box">
      <input v-model="newMemo" placeholder="메모를 입력하세요" />
      <button @click="addMemo">추가</button>
    </div>

    <ul class="memo-list">
      <MemoItem
        v-for="(memo, idx) in memos"
        :key="idx"
        :text="memo"
        @delete="deleteMemo(idx)"
      />
    </ul>

    <p v-if="memos.length === 0" class="empty">메모가 없습니다</p>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from "vue";
import MemoItem from "./components/MemoItem.vue";

const newMemo = ref("");
const memos = ref([]);

function addMemo() {
  if (newMemo.value.trim()) {
    memos.value.push(newMemo.value.trim());
    newMemo.value = "";
  }
}

function deleteMemo(index) {
  memos.value.splice(index, 1);
}

// ✅ localStorage 연동
onMounted(() => {
  const saved = localStorage.getItem("memos");
  if (saved) {
    memos.value = JSON.parse(saved);
  }
});

watch(
  memos,
  (newVal) => {
    localStorage.setItem("memos", JSON.stringify(newVal));
  },
  { deep: true }
);
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 40px auto;
  padding: 24px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
}

h2 {
  text-align: center;
  margin-bottom: 16px;
}

.input-box {
  display: flex;
  gap: 8px;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 10px;
  border-radius: 8px;
  border: 1px solid #ccc;
}

button {
  padding: 10px 14px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
}

button:hover {
  background-color: #369973;
}

.memo-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.empty {
  text-align: center;
  color: #aaa;
  margin-top: 20px;
}
</style>
