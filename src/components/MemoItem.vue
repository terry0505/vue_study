<template>
  <li class="memo-item" :class="{ done: memo.done }">
    <label class="checkbox-label">
      <input type="checkbox" :checked="memo.done" @change="$emit('toggle')" />
      <span class="text">{{ memo.text }}</span>
    </label>
    <button @click="$emit('delete')">삭제</button>
  </li>
</template>

<script setup>
defineProps({
  memo: Object
});
</script>


<style scoped>
.memo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #f9f9f9;
  border: 1px solid #ddd;
  padding: 10px 14px;
  margin-bottom: 10px;
  border-radius: 8px;
  font-size: 15px;
}

input[type="checkbox"] {
  width: 18px;
  height: 18px;
  accent-color: #42b983; 
  cursor: pointer;
}

.checkbox-label {
  display: flex;
  align-items: center;
  gap: 8px;
  flex: 1;
}

.text {
  word-break: break-all;
}

.memo-item.done .text {
  text-decoration: line-through;
  color: #aaa;
}

.memo-item button {
  background: #ff5c5c;
  color: white;
  border: none;
  padding: 6px 10px;
  border-radius: 6px;
  cursor: pointer;
}

.memo-item button:hover {
  background: #e04848;
}
</style>
