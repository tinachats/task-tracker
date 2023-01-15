<template>
    <li v-for="task in tasks" :key="task.id" :class="`task shadow-sm border ${task.background} ${task.reminder ? 'reminder' : ''}`" @toggle-reminder="$emit('toggle-reminder', task.id)" :style="`background-color: ${task.background}`">
        <Task @delete-task="$emit('delete-task', task.id)" @toggle-reminder="$emit('toggle-reminder', task.id)" :task="task" />   
    </li>
</template>

<script>
import Task from './Task.vue';
export default {
    name: 'Tasks',
    components: {
        Task,
    },
    props: {
        tasks: Array
    },
    emits: ['delete-task', 'toggle-reminder']
}
</script>

<style scoped>
.task{
    position: relative;
    list-style-type: none;
    border-radius: 1rem;
    margin-bottom: 1rem;
}

.task.reminder{
    border-left: 4px solid var(--bs-dark) !important;
}
</style>