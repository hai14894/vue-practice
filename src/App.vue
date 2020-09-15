<template>
  <div id='App'>
    <Todos/>

  </div>
  
</template>

<script>
import Todos from './components/Todo'

export default {
  name: 'App',
  components: {
    Todos
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
          completed: true
        },
        {
          id: 3,
          title : "task 3",
          completed: true
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
