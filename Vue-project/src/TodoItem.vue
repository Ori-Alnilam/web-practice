<script setup>
    const props = defineProps({
        todo: Object,
    })

    const emit = defineEmits(["removeTodo"])

    const removeItem = () => {
        emit("removeTodo", props.todo.id)
    }
</script>

<template>
    <li>
        <input type="checkbox" v-model="todo.done">
        <span :class="{done : todo.done}">Step {{ todo.id + 1 }}. {{ todo.text }}</span>
        <button @click="removeItem">X</button>
    </li>
</template>

<style scoped>
  .done {
    text-decoration: line-through;
  }
</style>