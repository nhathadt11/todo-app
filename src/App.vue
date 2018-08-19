<template>
  <div id="app">
    <TodoList :title="title" :todos="todos" />
    <AddTodo :todos="todos" />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import AddTodo from './components/AddTodo.vue'

export default {
  name: 'app',
  components: {
    TodoList,
    AddTodo,
  },
  data() {
    return {
      title: 'My Todo List',
      todos: [
        { id: 0, text: 'Task 1' },
        { id: 1, text: 'Task 2' },
        { id: 2, text: 'Task 3' },
      ]
    }
  }
}
</script>

<style>
</style>
