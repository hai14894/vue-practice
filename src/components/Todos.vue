<template>
  <div v-for="todo in todos" v-bind:key="todo.id">
    <TodoItem v-bind:todo="todo" @update-todo="update" v-on:is-completed="$emit('is-completed',todo.id)"/>
  </div>
</template>
<script>
import TodoItem from './TodoItem'
export default {
  name: "ToDos",
  props: ["todos"],
  components:{
      TodoItem
  },
  methods:{
      update(completed){
          this.todo.completed = completed
      }
  }
};
</script>

<style scoped>
</style>