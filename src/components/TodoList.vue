<template>
  <div>
    <h1 v-html="title" />
    <ul v-if="getFilteredTodos().length > 0">
      <li
        class="todo-item"
        v-bind:key="todo.id"
        v-for="todo in getFilteredTodos()"
      >
        <label :for="todo.id" v-html="todo.text" />
        <input
          type="checkbox"
          :id="todo.id"
          :checked="todo.complete"
          @click="() => toggleTodo(todo.id)"
        />
      </li>
    </ul>
    <p v-else>No todos.</p>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    title: { type: String, required: true },
    todos: { type: Array, required: true },
    currentFilter: { type: String, required: true },
  },
  methods: {
    getFilteredTodos() {
      switch (this.currentFilter) {
        case 'COMPLETE':
          return this.todos.filter(todo => todo.complete);
        case 'INCOMPLETE':
          return this.todos.filter(todo => !todo.complete);
        default:
          return this.todos;
      }
    },
    toggleTodo: function(id) {
      const selected = this.todos.find(todo => todo.id === id);
      selected.complete = !selected.complete;
    }
  }
}
</script>
<style>
.todo-item > * {
  cursor: pointer;
}
</style>
