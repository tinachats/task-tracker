<template>
    <div class="wrapper">
        <div class="p-3">
            <h6 class="lead fw-bold text-capitalize">
                {{ task.title }}
            </h6>
            <p class="small text-muted">{{ task.content }}</p>
            <a class="d-flex align-items-center small fw-bold text-capitalize mb-3" :href="`https://www.google.com/search?q=${task.location}`" target="_blank">
                <i class="bi-geo-alt me-1"></i> {{ task.location }}
            </a>
            <hr class="my-1">
            <div class="d-flex align-items-center">
                <i class="bi-clock"></i>
                <span class="ms-1 small-xs">{{ task.start }}</span>
                <span class="mx-1">-</span>
                <span class="small-xs">{{ task.end }}</span>
            </div>
        </div>
        <div :class="`task-actions shadow-sm ${task.background}`">
            <div class="d-flex flex-column justify-content-around h-100">
                <button class="btn btn-sm btn-danger rounded-circle" @click="deleteTask(task.id)">
                    <i class="bi-trash"></i>
                </button>
                <button class="btn btn-sm btn-primary rounded-circle" @click="editTask(task.id)">
                    <i class="bi-pencil"></i>
                </button>
                <button class="btn btn-sm btn-secondary rounded-circle" @click="shareTask(task.id)">
                    <i class="bi-share"></i>
                </button>
                <button class="btn btn-sm btn-light rounded-circle" @click="copyTask(task.id)">
                    <i class="bi-clipboard"></i>
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    methods: {
        deleteTask(id){
            console.log(id);
        },
        editTask(id){
            console.log(id);
        },
        shareTask(id){
            console.log(id);
        },
        copyTask(id){
            console.log(id);
        }
    }
}
</script>