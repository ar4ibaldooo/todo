<template>
    <li>
        <span v-bind:class="{done: todoItem.completed}">
            <input type="checkbox" v-on:change="markComplete">
            <strong>{{index + 1}}</strong>
            {{todoItem.title}}
        </span>
        <button class="rm" v-on:click="$emit('removeTodoItem', todoItem.id)">&times;</button>
    </li>
</template>
<script>
    export default {
        props: {
            todoItem: {
                type: Object,
                required: true
            },
            index: Number
        },
        data() {
            return {
                todoLocal: this.todoItem,
            };
        },
        methods: {
            markComplete() {
                this.todoLocal.completed = !this.todoLocal.completed;
            },
        },

    }

</script>
<style scoped>
    li {
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
    }
    .rm {
        background: rgba(255, 3, 0, 0.64);
        color: #fff;
        font-weight: 900;
    }
    .done {
        text-decoration: line-through;
    }
    input {
    margin-right: 1rem;
    }
</style>