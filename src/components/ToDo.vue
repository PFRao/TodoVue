<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <ToDoItem v-for='todo in todos' v-bind:todo='todo' v-bind:key='todo.id' v-on:delete='deleteTodo' v-on:renew='renewTodo' v-on:complete='completeTodo'></ToDoItem>
    <CreateTodo v-on:create='addTodo'></CreateTodo>
  </div>
</template>

<script type = "text/javascript" >
import ToDoItem from './ToDoItem'
import CreateTodo from './CreateTodo'

export default {
  props: {
    todos: Array
  },
  components: {
    ToDoItem,
    CreateTodo
  },
  methods: {
    deleteTodo (todo) {
      this.todos.splice(this.todos.indexOf(todo), 1)
    },
    addTodo (todo) {
      console.log('adding', todo)
      this.todos.push(todo)
    },
    renewTodo (todo) {
      this.todos[this.todos.indexOf(todo)].done = false
    },
    completeTodo (todo) {
      this.todos[this.todos.indexOf(todo)].done = true
    }
  }
}
</script>

<style>
</style>
