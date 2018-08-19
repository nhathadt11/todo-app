<template>
  <div id="app">
    <TodoList :title="title" :todos="todos" :currentFilter="currentFilter" />
    <AddTodo :todos="todos" />
    <FilterControl :currentFilter="currentFilter" :setFilter="setFilter" />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import AddTodo from './components/AddTodo.vue'
import FilterControl from './components/FilterControl.vue'

export default {
  name: 'app',
  components: {
    TodoList,
    AddTodo,
    FilterControl,
  },
  data() {
    return {
      title: 'My Todo List',
      todos: [
        { id: 0, text: 'Task 1', complete: true },
        { id: 1, text: 'Task 2', complete: false },
        { id: 2, text: 'Task 3', complete: false },
      ],
      currentFilter: 'ALL',
    }
  },
  methods: {
    setFilter(filter) {
      this.currentFilter = filter;
    },
  }
}
</script>

<style>
</style>
