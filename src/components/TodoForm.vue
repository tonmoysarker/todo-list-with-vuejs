<template>
    <form>
        <input type="text" id="todo-input" v-model="todoItem" />
        <button type="button" @click="handleAddItem">Add Item</button>
        <button type="button" @click="handleFilterItem">Filter Item</button>
    </form>
</template>

<script>
export default {
    emits: ["add-todo"],
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
            if (this.todoItem !== "") {
                this.$emit("add-todo", this.todoItem);
                this.todoItem = "";
            }
        },
    },
};
</script>

<style scoped>
form {
    border: 1px solid red;
    padding: 0.5rem;
    display: flex;
    justify-content: space-around;
    align-items: center;
}
</style>
