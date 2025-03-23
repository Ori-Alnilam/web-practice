<script setup>
  import { computed, ref } from "vue";

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

  const removeTodo = (todo) => {
    todos.value = todos.value.filter((e) => e !== todo)
  }

  const hideCompleted = ref(false)
  const filteredTodos = computed(() => {
    return hideCompleted.value
    ? todos.value.filter((e) => !e.done)
    : todos.value
  })

</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new Todo">
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="(todo, index) in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{done: todo.done}">Step {{ index + 1 }} : {{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  
  <!-- 练习计算属性 -->
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? "Show all" : "Hide completed" }}
  </button>
</template>

<style scoped>
  .done {
    text-decoration: line-through;
  }
</style>