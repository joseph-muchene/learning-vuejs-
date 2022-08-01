<template>
    <div v-bind:class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>
            {{ task.text }}
        </h3>

        <p>{{ task.day }}</p>


        <p @click="onDelete(task.id)" v-bind:style="{ color }">x</p>
    </div>
</template>


<script>
export default {
    name: "TaskItem",
    props: {
        task: Object,
        color: {
            type: String,
            default: "red"
        }
    },
    methods: {
        onDelete(id) {
            // emit event to the app level state
            // console.log(id)

            this.$emit('delete-task', id)
        }
    }
}

</script>


<style scope>
.fas {
    color: red;
}

.task {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}

.task.reminder {
    border-left: 5px solid green;
}

.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>
