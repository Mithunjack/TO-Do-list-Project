<template>
  <div id="app">
    <Todo v-bind:todos="todos" v-on:del-todo="deleteItem"></Todo>
  </div>
</template>

<script>
import Todo from "./components/Todo";
import axios from "axios";
export default {
  name: 'App',
  components: {
    Todo
  },
  data(){
    return {
      //without JSON Project
      todos : []
    }
  },
  methods: {
    deleteItem(id){
      this.todos =  this.todos.filter(todo => todo.id !== id);
    }
  },
  created() {
    axios.get("https://jsonplaceholder.typicode.com/todos?_limit=10")
            .then(res => this.todos = res.data )
            .catch(err => console.log(err));
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
  border: 1px solid darkgrey;
}
</style>
