<template>
  <div>
    <h1 v-html="title" />
    <ul>
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
    toggleTodo: function(id) { this.todos.forEach(todo => todo.id === id ? todo.complete = !todo.complete : todo) }
  }
}
</script>

