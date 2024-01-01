<template>
    <section>
        <ul v-auto-animate>
            <todo-list-item
                v-for="todo in todos"
                :key="todo.id"
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

<style scoped>
section ul {
    max-height: 17rem;
    list-style-type: none;
    padding: 0.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.7rem;
    align-items: center;
    justify-content: center;
    overflow-y: auto;
}
</style>
