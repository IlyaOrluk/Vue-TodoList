<template>
    <form>
        <input v-model="title"/>
        <button v-on:click="onSubmit" type='submit'>+</button>
    </form>
</template>
<script>
  export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()
            this.$emit('add-todo', this.title)
            this.title = ''
        }
    }
  }
</script>