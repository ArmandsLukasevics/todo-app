<template>
  <div class="todo-form">
    <form @submit.prevent="addTodo">
      <input type="text" placeholder="Add a task you need to do..." v-model="title" name="title" class="todo-input">
      <button type="submit" class="add-button">Add</button>
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    };
  },
  methods: {
    addTodo() {
      if (!this.title.trim()) return;
      const newTodoObj = {
        id: uuidv4(),
        title: this.title.trim(),
        completed: false
      };
      this.$emit('add-todo', newTodoObj);
      this.title = '';
    }
  }
};
</script>
