<script setup>
import { ref, reactive } from "vue";

const msg = ref("Vue");
const num = ref(0);
const newTodo = ref({});

const todoList = reactive([
  { name: "kiss", done: false },
  { name: "hug", done: false },
  { name: "sex", done: false },
]);

function increment() {
  num.value++;
}

function decrement() {
  num.value--;
}

const add = () => {
  todoList.push({ name: newTodo.value, done: false });
  newTodo.value = "";
};

const complete = (todo) => {
  todo.done = true;
};

const remove = (todo) => {
  const index = todoList.indexOf(todo);
  todoList.splice(index, 1);
};
</script>

<template>
  <div>
    Hello, {{ msg }}
    <button @click="increment">加一</button>
    <button @click="decrement">减一</button>
    <div>{{ num }}</div>
  </div>

  <div>
    <div>待办事项清单：</div>

    <input v-model="newTodo" placeholder="edit" />
    <button type="submit" @click="add">Add</button>
    <ul v-if="todoList.length > 0">
      <li v-for="(todo, index) in todoList">
        <span :class="{ 'delete-decoration': todo.done }"
          >{{ index }}. {{ todo.name }}</span>
        <span v-if="!todo.done">{{ index }}. {{ todo.name }}</span>
        <del v-if="todo.done">{{ index }}. {{ todo.name }}</del>
        <button @click="complete(todo)">complete</button>
        <button @click="remove(todo)">remove</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.delete-decoration {
  text-decoration: line-through;
}
</style>
