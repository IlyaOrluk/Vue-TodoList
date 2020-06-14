<template>
    <li>
        <input 
            type="checkbox"  
            v-bind:checked="todo.completed"  
            v-on:change="todo.completed = !todo.completed"
        />
        <div>
            <strong>{{ todo.id }}.</strong>
            <span
                v-bind:class="{done: todo.completed}"
            >{{ todo.title }}</span>
        </div>
        <button v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>
    li {   
        min-width: 60vw;
        border: 1px solid #666;
        display: flex;
        justify-content: space-between;
        margin: 1vh;
        padding: 1vh;
    }
    strong {
        margin: 1vh;
    }
    .done {
        text-decoration: line-through;
    }
</style>