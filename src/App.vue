<template>
    <main>
        <the-header></the-header>
        <todo-form @add-todo="addTodo" @filter-todo="filterTodo"></todo-form>
        <hr />
        <h3 v-if="todos.length === 0" class="msg">
            Add new items to the list!
        </h3>
        <todo-list :todos="todoList" v-else></todo-list>
    </main>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";
export default {
    name: "App",
    components: {
        TheHeader,
        TodoForm,
        TodoList,
    },
    provide() {
        return {
            removeTodo: this.removeTodo,
        };
    },
    data() {
        return {
            todos: [],
            filterText: "",
        };
    },
    computed: {
        todoList() {
            if (!this.filterText) {
                return this.todos;
            } else {
                return this.todos.filter((todo) =>
                    todo.toLowerCase().includes(this.filterText.toLowerCase())
                );
            }
        },
    },
    methods: {
        addTodo(todoItem) {
            this.todos.push(todoItem);
            this.filterText = "";
        },
        removeTodo(todoItem) {
            this.todos = this.todos.filter((todo) => todo !== todoItem);
        },
        filterTodo(filterItem) {
            this.filterText = filterItem;
            console.log(!this.filterText)
        },
    },
};
</script>

<style>
:root {
    --primary-color: hsl(267, 75%, 31%);
}
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

html {
    font-family: Arial, Helvetica, sans-serif;
}
body {
    width: 100%;
    height: 100vh;
}
main {
    width: 60%;
    height: 30rem;
    margin: 2rem auto;
    padding: 1rem;
    border-radius: 5px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
}

.msg {
    text-align: center;
    padding: 0.4rem;
    color: var(--primary-color);
}
</style>
