<template>
  <div id="app">
    <Todo v-bind:todos="todos" v-on:del-todo="deleteItem"></Todo>
  </div>
</template>

<script>
import Todo from "./components/Todo";
export default {
  name: 'App',
  components: {
    Todo
  },
  data(){
    return {
      todos : [
        {
          id : 1,
          title : "Todo one",
          completed : true
        },
        {
          id : 2,
          title : "Todo Two",
          completed : true
        },
        {
          id : 3,
          title : "Todo three",
          completed : false
        },
        {
          id : 4,
          title : "Todo four",
          completed : false
        },
      ]
    }
  },
  methods: {
    deleteItem(id){
      this.todos =  this.todos.filter(todo => todo.id !== id);
    }
  }
}
</script>

<style>
body{
  margin: 30px 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 500px;
  border: 1px solid darkgrey;
}
</style>
