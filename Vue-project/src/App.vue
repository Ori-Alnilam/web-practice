<script setup>
  import { ref } from "vue";
  import TodoList from "./TodoList.vue";

  let id = 0
  const todos = ref([
    { id: id++, text: "Learn HTML", done: true },
    { id: id++, text: "Learn JavaScript", done: true },
    { id: id++, text: "Learn Vue", done: false }
  ])

  const newTodo = ref("")
  const addTodo = () => {
    todos.value.push({ id: id++, text: newTodo.value, done: false })
    newTodo.value = ""
  }

  const remove = (id) => {
    todos.value = todos.value.filter((e) => e.id !== id)
  }
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new Todo">
    <button>Add Todo</button>
  </form>

  <TodoList :todos="todos" @delete-todo="remove"/>
</template>

<style scoped>
</style>