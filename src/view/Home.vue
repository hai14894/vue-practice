<template>
  <div></div>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:is-completed="isCompleted" v-on:delete="deleteItem"/>

  </div>
  
</template>

<script>
import Todos from '../components/Todos'
import AddTodo from '../components/AddToDo'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Todos,
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

      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log(err))
      
    },
    addTodo(newTodo){
      const {title, completed, id} = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed,
        id
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err))

    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
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
