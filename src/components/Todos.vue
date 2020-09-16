<template>
  <div v-for="todo in todos" v-bind:key="todo.id">
    <TodoItem v-bind:todo="todo"/>
  </div>
</template>
<script>
import TodoItem from './TodoItem'
export default {
  name: "ToDos",
  props: ["todos"],
  components:{
      TodoItem
  }
};
</script>

<style scoped>
</style>