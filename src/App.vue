<template>
    <main>
        <the-header></the-header>
        <todo-form @add-todo="addTodo"></todo-form>
        <hr />
        <todo-list :todos="todos"></todo-list>
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
            todos: ["dummy task1", "dummy task2", "dummy task3"],
        };
    },
    methods: {
        addTodo(todoItem) {
            console.log(this.todos);
            this.todos.push(todoItem);
        },
        removeTodo(todoItem) {
            this.todos = this.todos.filter((todo) => todo !== todoItem);
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
    margin: auto;
    padding: 1rem;
    border-radius: 5px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
}
</style>
