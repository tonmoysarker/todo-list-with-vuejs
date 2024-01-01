<template>
    <li>
        <p>{{ receivedTodo }}</p>
        <span @click="removeTodo(receivedTodo)">&times;</span>
    </li>
</template>

<script>
export default {
    inject: ["removeTodo"],
    props: {
        receivedTodo: {
            type: String,
            required: true,
        },
    },
};
</script>

<style scoped>
li {
    width: 95%;
    min-height: 3rem;
    padding: 0.5rem;
    display: flex;
    align-items: center;
    justify-content: start;
    gap: 0.5rem;
    font-size: 1.2rem;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}

li p {
    display: inline-block;
    width: 90%;
}
li span {
    display: inline-block;
    font-size: 1.8rem;
    cursor: pointer;
}

li span:hover {
    font-size: 2rem;
    font-weight: bold;
    color: red;
}
</style>
