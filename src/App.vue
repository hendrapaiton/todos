<script setup lang="ts">
import { ref } from 'vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'

const todos = ref<string[]>([])

function addTodo(todo: string) {
  todos.value.push(todo)
}

function removeTodo(index: number) {
  todos.value.splice(index, 1);
}
</script>

<template>
  <div class="app-container">
    <h1>UKOM XII RPL SMKNJ 2025</h1>
    <TodoInput @add-todo="addTodo" />
    <TodoList :todos="todos" @remove-todo="removeTodo" />
  </div>
</template>

<style scoped>
.app-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #f9f9f9;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

h1 {
  text-align: center;
  color: #333;
}
</style>
