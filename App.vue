<template>
  <div id="app">
    <h1>Todo application</h1>
    <AddTodo 
    @add-todo="AddTodo"/>
    <hr>
    <TodoList 
    v-bind:todos="todos"
    @remove-todo="removeTodo"
    
    />
  </div>
</template>

<script>

import TodoList from './components/TodoList.vue'
import AddTodo from './components/AddTodo.vue'
export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'Выучить Javascript', completed: false},
        {id: 2, title: 'Выучить Vue', completed: false},
        {id: 3, title: 'Выучить Английский', completed: false},
      ]
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
  .then(response => response.json())
  .then(json => { this.todos = json})
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !=id)
    },
    AddTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList,
    AddTodo

}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
