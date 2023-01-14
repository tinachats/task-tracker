<template>
    <div class="d-flex align-items-center justify-content-between">
        <div class="d-block">
            <h6 class="lead text-muted text-capitalize mb-0">{{ date }}</h6>
            <h4 class="fw-bold text-capitalize mt-0">today</h4>
        </div>
        <button class="btn btn-dark rounded-pill">
            <div class="d-flex align-items-center justify-content-center fw-bold">
                <i class="bi-plus"></i> Add task
            </div>
        </button>
    </div>
</template>

<script>
   export default {
    name: 'Header',
    data(){
        return{
            date: this.todaysDate()
        }
    },
    methods: {
        todaysDate(){
            const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
            const dt = new Date();
            return(`
               ${months[dt.getMonth()]} ${dt.getDate()}, ${dt.getFullYear()}
            `);
        }
    }
   }
</script>