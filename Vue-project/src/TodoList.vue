<script setup>
    import TodoItem from './TodoItem.vue';

    const props = defineProps({
        todos: Object
    })

    const emit = defineEmits(["deleteTodo"])

    const deleteItem = (id) => {
        emit("deleteTodo", id)
    }
</script>

<template>
    <ul>
        <TodoItem v-for="(todo, index) in todos"
            :todo="todo"
            :key="todo.id"
            @remove-todo="deleteItem(todo.id)"
        />
    </ul>
</template>