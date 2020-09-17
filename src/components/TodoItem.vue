<template>
  <div v-bind:class="{'is-completed':todo.completed}">
    <p>
      <input type="checkbox" @change="$emit('is-completed', todo.id)" />
      {{todo.title}}
      <button @click="$emit('delete', todo.id)">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"]
  
};
</script>

<style scoped>
.is-completed {
  text-decoration: line-through;
}
</style>