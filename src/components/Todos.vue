<template>
  <div v-for="todo in todos" v-bind:key="todo">
    <h3>{{todo.title}}</h3>
  </div>
</template>
<script>
export default {
  name: "ToDos",
  props: ["todos"]
};
</script>

<style scoped>
</style>