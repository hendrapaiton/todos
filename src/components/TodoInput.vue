<script setup lang="ts">
import { ref, defineEmits } from 'vue'

const newTodo = ref('')
const emit = defineEmits(['add-todo'])

function submitTodo() {
  if (newTodo.value.trim()) {
    emit('add-todo', newTodo.value)
    newTodo.value = ''
  }
}
</script>

<template>
  <div class="todo-input">
    <input v-model="newTodo" @keyup.enter="submitTodo" placeholder="Add a todo" />
    <button @click="submitTodo">Add</button>
  </div>
</template>

<style scoped>
.todo-input {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  background-color: #28a745;
  color: white;
  cursor: pointer;
}

button:hover {
  background-color: #218838;
}
</style>
