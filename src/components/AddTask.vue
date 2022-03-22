<template>
    <form @submit="submitTask" id="save-task" class="needs-validation">
        <div class="form-floating my-2">
            <input type="text" class="form-control rounded-pill" v-model="title" name="title" id="add-task" placeholder="eg. Doctor's appointment">
            <label for="add-task">Add Task</label>
        </div>
        <div class="form-floating">
            <input type="text" class="form-control rounded-pill" v-model="day" name="day" id="day" placeholder="Password">
            <label for="day">Add Day & Time</label>
        </div>
        <div class="form-check w-30 m-3">
            <input class="form-check-input" type="checkbox" value="" v-model="reminder" name="reminder" id="reminder">
            <label class="form-check-label text-start" for="reminder">
                Set Reminder
            </label>
        </div>
        <div class="text-end">
            <button type="submit" class="btn btn-success rounded-pill px-4">
                Save Task
            </button>
        </div>
    </form>
</template>

<style>
    .w-30{
        width: 30% !important;
    }
</style>

<script>
    export default{
        name: 'AddTask',
        data(){
            return{
                title: '',
                day: '',
                reminder: false
            }
        },
        methods: {
            submitTask(e){
                e.preventDefault();
                
                if(!this.title){
                    alert('Please add a task');
                    return;
                }

                const newTask = {
                    id: Math.floor(Math.random() * 100000),
                    title: this.title,
                    day: this.day,
                    reminder: this.reminder
                }

                this.$emit('add-task', newTask);

                this.title = '';
                this.day = '';
                this.reminder = false
            }
        },
    }
</script>