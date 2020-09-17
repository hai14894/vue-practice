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

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title : "task 1",
          completed: false
        },
        {
          id: 2,
          title : "task 2",
          completed: false
        },
        {
          id: 3,
          title : "task 3",
          completed: false
        }
      ]
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
