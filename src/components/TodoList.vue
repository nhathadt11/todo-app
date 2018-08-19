<template>
  <div>
    <h1 v-html="title" />
    <ul>
      <li
        v-bind:key="todo.id"
        v-for="todo in getFilterTodos()"
        v-html="todo.text"
      />
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    title: String,
    todos: Array,
    currentFilter: String,
  },
  methods: {
    getFilterTodos() {
      switch (this.currentFilter) {
        case 'COMPLETE':
          return this.todos.filter(todo => todo.complete);
        case 'INCOMPLETE':
          return this.todos.filter(todo => !todo.complete);
        default:
          return this.todos;
      }
    },
  }
}
</script>

