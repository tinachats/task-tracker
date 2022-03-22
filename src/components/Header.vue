<template>
    <div class="d-flex align-items-center justify-content-between">
        <h1 class="fs-2">{{ title }}</h1>
        <Button @toggle-add-task="$emit('toggle-add-task')" :btnText="showAddTask ? 'Close' : 'Add Task'" :btnColor="showAddTask ? '#0a58ca' : '#0d6efd'" />
    </div>
</template>

<script>
    import Button from './Button.vue'

    export default{
        name: 'Header',
        props: {
            title: {
                type: String,
                default: 'Task Management App'
            }, 
            showAddTask: Boolean
        },
        components: {
            Button,
        }
    }
</script>