<template>
    <div>

        <div class="title-item" v-bind:class="{'completed-task' : todo.completed }" >
            <input type="checkbox" v-on:change="clicked">
            {{todo.title}}
            <button class="delete-button btn" v-on:click="$emit('del-todo',todo.id)">Delete</button>
        </div>

    </div>
</template>

<script>
    export default {
        name: "ToDoItem",
        props:["todo"],
        methods: {
            clicked(){
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    .title-item{
        margin: 15px;
        padding: 30px;
        border: 1px solid white;
        box-shadow: 1px 2px 10px 0px #888888;
        font-size: 24px;
    }
    .completed-task{
        text-decoration: line-through;
        color: blueviolet;
    }
    .delete-button{
        float: right;
        color: red;
        padding: 10px;
        border-radius: 5px;
        cursor: pointer;
        margin-left: 15px;
    }
</style>