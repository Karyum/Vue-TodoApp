<template>
  <div :class="{deleted: todo.deleted}">
    <h3
      @click="emitComplete(todo)"
      :class="{completed: todo.completed}">
      {{ todo.description }}
    </h3>
    <button
      v-if="todo.description"
      :class="{filterOn: todo.hideButton}"
      type="button"
      @click="emitDelete(todo)">
      Delete
    </button>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  methods: {
    emitDelete(todo) {
      this.$emit('delete-todo', todo);
    },
    emitComplete(todo) {
      this.$emit('complete-todo', todo);
    }
  }
};
</script>

<style scoped>

.completed {
  text-decoration: line-through;
}

.deleted {
  display: none;
}

h3 {
  cursor: pointer;
  user-select: none;
}

.filterOn {
  display: none;
}

</style>
