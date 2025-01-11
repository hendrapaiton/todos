<script setup lang="ts">
import type { PropType } from 'vue'
import { defineEmits } from 'vue';

defineProps({
  todos: {
    type: Array as PropType<string[]>,
    required: true,
  },
});

const emit = defineEmits(['remove-todo']);

function remove(index: number) {
  emit('remove-todo', index);
}

function toggleComplete(event: Event) {
  const target = event.target as HTMLElement;
  target.classList.toggle('completed');
}
</script>

<template>
  <ul class="todo-list">
    <li v-for="(todo, index) in todos" :key="index" @click="toggleComplete">
      {{ todo }}
      <button @click.stop="remove(index)" class="remove-btn">x</button>
    </li>
  </ul>
</template>

<style scoped>
.todo-list {
  list-style-type: none;
  padding: 0;
}

.todo-list li {
  padding: 10px;
  border-bottom: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
}

.todo-list li:last-child {
  border-bottom: none;
}

.todo-list li.completed {
  text-decoration: line-through;
  color: #888;
}

.remove-btn {
  background-color: #ff4d4d;
  border: none;
  border-radius: 4px;
  color: white;
  cursor: pointer;
  padding: 5px 10px;
}

.remove-btn:hover {
  background-color: #ff1a1a;
}
</style>
