<template>
  <div class="filter-container">
    <a href="#" class="filter" v-bind:class="{ active: currentFilter === 'ALL' }" @click="() => setFilter('ALL')">All</a>
    <a href="#" class="filter" v-bind:class="{ active: currentFilter === 'COMPLETE' }" @click="() => setFilter('COMPLETE')">Complete</a>
    <a href="#" class="filter" v-bind:class="{ active: currentFilter === 'INCOMPLETE' }" @click="() => setFilter('INCOMPLETE')">Incomplete</a>
  </div>
</template>

<script>
export default {
  name: 'FilterControl',
  props: {
    currentFilter: { type: String, required: true },
    setFilter: { type: Function, required: true },
  }
} 
</script>

<style>
.filter-container {
  margin: 10px 0;
}
.filter {
  padding: 0 10px;
  position: relative;
}
.filter:not(:last-child)::after {
  content: '';
  position: absolute;
  right: 0;
  width: 1px;
  height: 100%;
  background-color: #000;
}
.filter.active {
  pointer-events: none;
  text-decoration: none;
  color: #000;
}
</style>
