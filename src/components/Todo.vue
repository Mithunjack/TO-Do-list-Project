<template>
    <div>
        <Header></Header>
        <AddTodo v-on:add-Todo="addTodo"></AddTodo>
        <div v-bind:key="todo.id" v-for="todo in todos">
           <ToDoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)" ></ToDoItem>
        </div>
    </div>
</template>

<script>
    import ToDoItem from "./ToDoItem";
    import Header from "./layout/Header";
    import AddTodo from "./AddTodo";
    export default {
        name: "Todo",
        components: {
            AddTodo,
            Header,
            ToDoItem
        },
        props:["todos"],
        methods: {
            addTodo(newTodo){
                this.todos = [...this.todos , newTodo]
            }
        }
    }
</script>

<style scoped>

</style>