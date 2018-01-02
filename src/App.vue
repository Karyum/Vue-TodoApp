<template>
  <div id="app">

    <add-todo :todos="todos"></add-todo>

      <todo-list
        :allTodos="todos"
        :filter="currentFilter"
        :todos="filterTodos"
        @change-filter="changeFilter">
      </todo-list>
  </div>
</template>

<script>
import TodoList from './components/todo-list.vue';
import AddTodo from './components/add-todo.vue';

export default {
  components: {
    'todo-list': TodoList,
    'add-todo': AddTodo
  },
  name: 'app',
  data() {
    return {
      todos: [
        {
          description: 'Go to sleep Mario',
          id: 1,
          completed: false,
          deleted: false
        },
        {
          description: 'For real though go to sleep',
          id: 2,
          completed: false,
          deleted: false
        },
        {
          description: 'you love sleeping',
          id: 3,
          completed: false,
          deleted: false
        }
      ],
      currentFilter: 'ALL'
    };
  },
  methods: {
    changeFilter(newFilter) {
      this.currentFilter = newFilter;
    }
  },
  computed: {
    filterTodos: function() {
      switch (this.currentFilter) {
        case 'ALL':
          return this.todos;
        case 'COMPLETED':
          return this.todos.filter(todo => todo.completed);
        case 'DELETED':
          return this.todos.map(
            todo =>
              todo.deleted && {
                description: todo.description,
                hideButton: true
              }
          );
        default:
          return this.todos;
      }
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
