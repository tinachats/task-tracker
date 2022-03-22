<template>
    <ul class="list-group shadow-sm rounded-3 my-3">
        <li class="list-group-item" v-for="task in tasks" :key="task.id">
            <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task" />
        </li>
    </ul>
</template>

<script>

import Task from './Task'

export default{
    name: 'Tasks',
    props: {
        tasks: Array
    },
    components: {
        Task
    }
}
</script>
