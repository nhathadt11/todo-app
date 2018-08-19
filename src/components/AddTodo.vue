<template>
  <div>
    <input type="text" v-model="text">
    <button @click="addTodo" :disabled="!text">Add</button>
  </div>
</template>
<script>
export default {
  name: 'AddTodo',
  props: {
    todos: { type: Array, required: true },
  },
  data() {
    return {
      text: undefined,
    }
  },
  methods: {
    addTodo() {
      const length = this.todos.length;
      this.todos.push({ id: length, text: this.text, complete: false });
      this.text = undefined;
    }
  }
}
</script>
