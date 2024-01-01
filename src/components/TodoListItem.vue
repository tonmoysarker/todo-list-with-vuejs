<template>
    <li>{{ todo }} <span>&times;</span></li>
</template>

<script>
export default {
    props: {
        receivedTodo: {
            type: String,
            required: true,
        },
    },
    data() {
        return {
            todo: this.receivedTodo,
        };
    },
};
</script>
