<template>
  <div class="">
    <h4>Filter: {{ filter }}</h4>
    <button type="button" @click="emitFilterChange('COMPLETED')">Show completed</button>
    <button type="button" @click="emitFilterChange('ALL')">Show all</button>
    <button type="button" @click="emitFilterChange('DELETED')">Show deleted</button>
    <div>
      <Todo
        v-for="todo in todos"
        :todo="todo"
        :key="todo.id"
        @delete-todo="deleteTodo"
        @complete-todo="completeTodo"
      ></Todo>
    </div>
  </div>
</template>

<script>
import Todo from './todo.vue';

export default {
  props: ['todos', 'allTodos', 'filter'],
  components: {
    Todo
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.allTodos.indexOf(todo);
      this.allTodos[todoIndex].deleted = true;
    },
    completeTodo(todo) {
      const todoIndex = this.allTodos.indexOf(todo);
      this.allTodos[todoIndex].completed = !this.allTodos[todoIndex].completed;
    },
    emitFilterChange(filter) {
      this.$emit('change-filter', filter);
    }
  }
};
</script>

<style scoped>

</style>
