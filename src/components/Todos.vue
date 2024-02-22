<script>
import Todo from "@/components/Todo.vue";
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Todos',
  components: {
    Todo
  },
  props: [
    "todos"
  ]
}
</script>

<template>
  <div>
    <h2>My TODO list</h2>
    <ul>
      <li v-bind:key="todo.id" v-for="todo in todos">
        <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"/>
      </li>
    </ul>
  </div>
</template>

<style scoped>

</style>