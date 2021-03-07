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
  max-width: 900px;
  color: #2c3e50;
  margin: 0 auto;
  line-height: 2.5;
}

h1 {
    text-align: center;
}

table {
    border-collapse: collapse;
    border: 2px solid rgb(200,200,200);
    letter-spacing: 1px;
    font-size: 0.8rem;
    margin: 20px 0;
}

td, th {
    border: 1px solid rgb(190,190,190);
    padding: 10px 20px;
}

th {
    background-color: rgb(235,235,235);
}
  
td {
    text-align: center;
}

tr:nth-child(even) td {
    background-color: rgb(250,250,250);
}

tr:nth-child(odd) td {
    background-color: rgb(245,245,245);
}

tr:hover td {
    background-color: #9bf0c9;
    color: #000;
}

caption {
    padding: 10px;
}

</style>
