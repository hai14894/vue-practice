<template>
  <div id='App' >
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:is-completed="isCompleted" v-on:delete="deleteItem"/>

  </div>
  
</template>

<script>
import Todos from './components/Todos'
import AddTodo from './components/AddToDo'
import Header from './components/layout/Header'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods:{
    isCompleted(id) {
      this.todos[id - 1].completed = !this.todos[id - 1].completed
    },
    deleteItem(id){
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo];
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos')
        .then(response => this.todos = response.data.map(item => ({...item, completed: false})))
        .catch(e => console.log(e))
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;

}


</style>
