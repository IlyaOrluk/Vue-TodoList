<template>
  <div id="app">
    <h1>Todo application</h1>
    <TodoForm 
      @add-todo="addTodo"
    />
    <hr/>
    <TodoList
      v-if="todos.length"
      v-bind:todos="todos"
      @remove-todo="removeTodo"
    />
    <h3 v-else>Not todo...</h3>
    <router-view/>
  </div>
</template>

<script>
  import TodoList from '@/components/TodoList'
  import TodoForm from '@/components/TodoForm'

  export default {
    name: 'App',
    data() {
      return {
        todos: [

        ]
      }
    },
    mounted() {
      fetch('https://jsonplaceholder.typicode.com/todos')
      .then(response => response.json())
      .then(json => console.log(json))

    },
    components: {
      TodoList,
      TodoForm
    },
    methods: {
      removeTodo(id) {
        this.todos = this.todos.filter(i => i.id !== id)
      },
      addTodo(title) {
        this.todos = [...this.todos, { id: this.todos.length+1, title: title, completed: false }]
      }
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
