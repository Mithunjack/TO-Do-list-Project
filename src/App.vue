<template>
  <div id="app">
    <Header></Header>
    <AddTodo v-on:add-Todo="addTodo"></AddTodo>
    <Todo v-bind:todos="todos" v-on:del-todo="deleteItem"></Todo>
  </div>
</template>

<script>
import Todo from "./components/Todo";
import axios from "axios";
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";
export default {
  name: 'App',
  components: {
    AddTodo,
    Header,
    Todo
  },
  data(){
    return {
      //without JSON Project
      todos : []
    }
  },
  methods: {
    addTodo(newTodo){
      const {title , completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos',{title,completed})
              .then(res => this.todos = [...this.todos , res.data])
              .catch(err => console.log(err));

      console.log(this.todos)

    },
    deleteItem(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
              .then(() => this.todos =  this.todos.filter(todo => todo.id !== id))
              .catch(err => console.log(err));

    }
  },
  created() {
    axios.get("https://jsonplaceholder.typicode.com/todos?_limit=5")
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
