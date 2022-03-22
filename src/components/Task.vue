<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task d-flex align-items-center justify-content-between']" title="Double click task to change reminder">
        <div class="d-block text-start ms-3">
            <h6 class="fw-bold my-0">{{ task.title }}</h6>
            <small class="text-muted my-0 py-0">{{ task.day }}</small>
        </div>
        <div class="me-3">
            <button @click="onDelete(task.id)" class="btn btn-light btn-sm rounded-circle d-grid">
                <i class="bi bi-trash m-auto"></i>
            </button>
        </div>
    </div>
</template>

<style scoped>
    .task.reminder{
        border-left: 5px solid var(--bs-success);
    }
</style>

<script>
    export default{
        name: 'Task',
        props: {
            task: Object
        },
        methods: {
            onDelete(id){
                this.$emit('delete-task', id);
            }
        },
        emits: ['delete-task', 'toggle-reminder']
    }
</script>