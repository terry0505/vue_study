<template>
  <li class="item">
    <span>{{ item }}</span>
    <button class="delete" @click="$emit('remove')">삭제</button>
  </li>
</template>

<script setup>
defineProps({
  item: String
});
</script>

<style scoped>
.item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #f9f9f9;
  border: 1px solid #ddd;
  padding: 8px 12px;
  margin-bottom: 8px;
  border-radius: 6px;
}

.delete {
  background: #ff5c5c;
  color: white;
  border: none;
  padding: 4px 8px;
  border-radius: 4px;
  cursor: pointer;
}

.delete:hover {
  background: #e04848;
}
</style>
