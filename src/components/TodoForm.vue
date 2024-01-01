<template>
    <div class="todo-form">
        <input
            type="text"
            id="todo-input"
            v-model.trim="todoItem"
            placeholder="type your task here"
            @input="handleFilterItem"
        />
        <div class="button-container">
            <button class="btn" type="button" @click="handleAddItem">
                Add Item
            </button>
        </div>
    </div>
</template>

<script>
export default {
    emits: ["add-todo", "filter-todo"],
    data() {
        return {
            todoItem: "",
        };
    },
    methods: {
        handleAddItem() {
            if (this.todoItem !== "") {
                this.$emit("add-todo", this.todoItem);
                this.todoItem = "";
            }
        },
        handleFilterItem() {
            // Handle filter logic here
            if (this.todoItem !== "") {
                this.$emit("filter-todo", this.todoItem);
            }
        },
    },
};
</script>

<style scoped>
.todo-form {
    padding: 0.5rem;
    margin-bottom: 1rem;
    display: flex;
    flex-direction: column; /* Stacks items vertically */
    align-items: center; /* Centers items horizontally */
}

#todo-input {
    width: 20rem;
    height: 2rem;
    font-size: 1rem;
    padding: 0.5rem;
    margin-bottom: 1rem; /* Adds space between input and buttons */
    border: none;
    box-shadow: 0 2px rgba(0, 0, 0, 0.5);
}

#todo-input:focus {
    background-color: rgba(161, 134, 191, 0.2);
    outline: none;
    border: 2px solid var(--primary-color);
    border-radius: 5px;
}

.button-container {
    display: flex;
    gap: 1rem;
}

.btn {
    background-color: var(--primary-color);
    color: #fff;
    font-size: 1rem;
    padding: 0.3rem 1rem;
    cursor: pointer;
    border: none;
    border-radius: 6px;
    box-shadow: 0 4px rgba(0, 0, 0, 0.5);
    transition: background-color 0.3s ease;
}

.btn:hover {
    background-color: #fff;
    color: var(--primary-color);
    outline: 1px solid var(--primary-color);
}

.btn:active {
    box-shadow: 0 2px rgba(0, 0, 0, 0.5);
    transform: translateY(2px);
}
/* Responsive design for mobile devices */
@media (max-width: 768px) {
    .todo-form {
        flex-direction: column; /* Stacks items vertically */
        align-items: center; /* Centers items horizontally */
    }

    #todo-input {
        width: 100%; /* Takes full width of the container */
        max-width: 20rem; /* Maximum width for larger screens */
    }

    .button-container {
        flex-direction: column; /* Stacks buttons vertically */
        gap: 0.5rem; /* Adds space between buttons */
    }
}
</style>
