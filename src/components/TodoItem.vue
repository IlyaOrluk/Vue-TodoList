<template>
    <div>
        <li>{{ todo.title }}</li>
    </div>
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