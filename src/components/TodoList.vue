<template>
  <div>
    <h1 v-html="title" />
    <ul v-if="getFilterTodos().length > 0">
      <li
        v-bind:key="todo.id"
        v-for="todo in getFilterTodos()"
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
    toggleTodo: function(id) {
      const selected = this.todos.find(todo => todo.id === id);
      selected.complete = !selected.complete;
    }
  }
}
</script>

