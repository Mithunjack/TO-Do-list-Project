<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todos">
           <ToDoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)" ></ToDoItem>
        </div>
    </div>
</template>

<script>
    import ToDoItem from "./ToDoItem";
    export default {
        name: "Todo",
        components: {
            ToDoItem
        },
        props:["todos"]
    }
</script>

<style scoped>

</style>