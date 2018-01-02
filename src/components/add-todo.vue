<template>
  <div>
    <label>
      <input
        v-model="newTodo"
        @keyup.enter="addTodo"
        type="text" />
    </label>
  </div>
</template>

<script>
export default {
  props: ['todos'],
  data() {
    return {
      num: 3,
      newTodo: ''
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        description: this.newTodo,
        id: this.num + 1,
        completed: false,
        deleted: false
      });
      this.num = this.num + 1;
      this.newTodo = '';
    }
  }
};
</script>

<style scoped>

</style>
