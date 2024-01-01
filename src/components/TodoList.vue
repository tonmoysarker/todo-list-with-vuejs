<template>
    <section>
        <ul v-auto-animate>
            <todo-list-item
                v-for="todo in todos"
                :key="todo"
                :received-todo="todo"
            ></todo-list-item>
        </ul>
    </section>
</template>

<script>
import TodoListItem from "./TodoListItem.vue";
export default {
    components: {
        TodoListItem,
    },
    props: {
        todos: {
            type: Array,
            required: true,
        },
    },
    data() {
        return {};
    },
};
</script>

<style scoped></style>
