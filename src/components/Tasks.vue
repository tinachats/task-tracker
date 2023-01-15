<template>
    <li v-for="task in tasks" :key="task.id" :class="`task shadow-sm border ${task.background} ${task.reminder ? 'reminder' : ''}`">
        <Task :task="task" />   
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
    }
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