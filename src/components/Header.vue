<template>
    <div class="d-flex align-items-center justify-content-between">
        <div class="d-block">
            <h6 class="lead text-muted text-capitalize mb-0">{{ date }}</h6>
            <h4 class="fw-bold text-capitalize mt-0">today</h4>
        </div>
        <Button @btn-click="$emit('toggle-add-task')" :btnType="showAddTask ? 'btn-outline-dark' : 'btn-dark'" :btnText="showAddTask ? 'Hide task form' : 'Show task form'" :btnIcon="showAddTask ? 'bi-chevron-up' : 'bi-chevron-down'" />
    </div>
</template>

<script>
   import Button from './Button.vue';

   export default {
    name: 'Header',
    props: {
        showAddTask: Boolean
    },
    components: {
    Button,
    },
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