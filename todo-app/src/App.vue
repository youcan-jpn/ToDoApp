<template>
  <div id="app">
      <h1>Todo App!</h1>
      <TodoList/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  color: #2c3e50;
  margin: 0 auto;
  line-height: 2.5;
}

h1 {
    text-align: center;
}
</style>
