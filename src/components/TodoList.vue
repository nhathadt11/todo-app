<template>
  <div>
    <h1 v-html="title" />
    <ul>
      <li
        v-bind:key="todo.id"
        v-for="todo in todos"
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
  }
}
</script>

