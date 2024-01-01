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

<style scoped>
section{
    height: 17rem;
    overflow: hidden;
    overflow-y: auto;
} 

section ul{
    list-style-type: none;
    padding: 0.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.7rem;
    align-items: center;
    justify-content: center;
}
</style>
