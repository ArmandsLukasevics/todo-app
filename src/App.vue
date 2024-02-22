<template>
  <div id="app" class="app-container">
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>
<script>
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
export default {
  name: 'app',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  created() {
    const storedTodos = localStorage.getItem('todos');
    if (storedTodos) {
      this.todos = JSON.parse(storedTodos);
    }
  },
  methods: {
    addTodo(newTodoObj) {
      this.todos = [...this.todos, newTodoObj];
      localStorage.setItem('todos', JSON.stringify(this.todos));
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
      localStorage.setItem('todos', JSON.stringify(this.todos));
    }
  }
}
</script>
<style>
</style>