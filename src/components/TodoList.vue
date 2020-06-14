<template>
    <div>
        <ul>
            <TodoItem 
                v-for="todo in todos"
                :key="todo.id"
                v-bind:todo="todo"
                v-on:remove-todo="removeTodo"
            />
        </ul>
    </div>
</template>
<script>
  import TodoItem from '@/components/TodoItem'

  export default {
    props: ['todos'],
    components: {
      TodoItem
    },
    methods: {
        removeTodo(id) {
            this.$emit('remove-todo', id)
        }
    }
  }
</script>
<style scoped>
    ul {
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 0;
    }
</style>