<template>
  <li class="memo-item">
    <span>{{ text }}</span>
    <button @click="$emit('delete')">삭제</button>
  </li>
</template>
<script setup>
defineProps({
  text: String
});
</script>
<style scoped>
.memo-item {
  display: flex;
  justify-content: space-between;
  background: #f9f9f9;
  border: 1px solid #ddd;
  padding: 10px 14px;
  margin-bottom: 10px;
  border-radius: 8px;
  font-size: 15px;
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
