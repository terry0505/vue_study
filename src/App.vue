<template>
  <div class="container">
    <h2>📝 나의 Todo 리스트</h2>
  </div>
  <div class="form">
    <input v-model="newTodo" placeholder="할 일을 입력하세요" />
    <button @click="addTodo">추가</button>
  </div>
  <ul class="list">
    <TodoItem
      v-for="(todo, index) in todos"
      :key="index"
      :item="todo"
      @remove="removeTodo(index)"
    />
  </ul>
  <p v-if="todos.length === 0" class="empty">할 일이 없습니다.</p>
</template>

<script setup>
import { ref } from "vue";
import TodoItem from "./components/TodoItem.vue";

const newTodo = ref("");
const todos = ref(["Vue 공부하기", "밥 먹기"]);

function addTodo() {
  if (newTodo.value.trim()) {
    todos.value.push(newTodo.value);
    newTodo.value = "";
  }
}

function removeTodo(index) {
  todos.value.splice(index, 1);
}
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: 40px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
  background: #fff;
}

h2 {
  text-align: center;
  margin-bottom: 16px;
  color: #333;
}

.form {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}

input {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 6px;
}

button {
  padding: 8px 12px;
  border: none;
  background-color: #42b883;
  color: white;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background-color: #369973;
}

.list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.empty {
  text-align: center;
  color: #999;
  font-style: italic;
}
</style>
