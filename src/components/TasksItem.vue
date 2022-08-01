<template>

    <div v-for="task in tasks" v-bind:key="task.id">

        <SingleItem v-bind:task="task" @delete-task="$emit('delete-task', task.id)" />

    </div>

</template>

<script>
import SingleItem from './TaskItem.vue'

export default {
    name: "TaskItem",
    props: {
        tasks: Array
    },
    components: {
        SingleItem
    },
    emits: ['delete-task']
}

</script>