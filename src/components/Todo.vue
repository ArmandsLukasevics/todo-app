<template>
  <div v-bind:class="{'completed': todo.completed}" class="todo-container">
    <p v-on:click="markComplete" class="todo-text">{{ todo.title }}</p>
    <button @click="$emit('delete-todo', todo.id)" class="delete-button">Delete TODO</button>
  </div>
</template>
<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Todo',
  props: [
    "todo"
  ],
  methods:{
    markComplete(){
      // eslint-disable-next-line vue/no-mutating-props
      this.todo.completed = !this.todo.completed
    }
  }
}
</script>