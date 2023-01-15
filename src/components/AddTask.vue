<template>
    <h2 class="fw-bold">Create task</h2>
    <hr>
    <form @submit="addTask" method="post" class="row align-items-md-end g-3 my-2 needs-validation" novalidate>
        <div class="col-9">
            <div class="form-group">
                <label for="phone_number" class="fw-bold">Title</label>
                <input type="text" class="form-control text-capitalize" name="title" id="title" placeholder="Title" v-model="title" required autofocus>
                <small class="invalid-feedback fw-bold">Title is required!</small>
            </div>
        </div>
        <div class="col-2">
            <div class="form-group">
                <input type="color" class="form-control form-control-color text-capitalize" name="background" id="background" data-bs-toggle="tooltip" data-bs-placement="bottom" title="Choose your color" v-model="background">
            </div>
        </div>
        <div class="form-group">
            <label for="location" class="fw-bold">Location</label>
            <input type="text" class="form-control text-capitalize" name="location" id="location" placeholder="Location" v-model="location">
        </div>
        <div class="col-12 d-flex align-items-center justify-content-between">
            <label class="form-check-label text-start fw-bold ms-0" for="all-day">All day</label>
            <div class="form-check form-switch">
                <input class="form-check-input ms-auto" type="checkbox" role="switch" id="all-day" v-model="allDay">
            </div>
        </div>
        <div class="col-12 col-md-6">
            <div class="form-group">
                <label for="start-date" class="fw-bold">Start Date</label>
                <input type="date" class="form-control" name="start-date" id="start-date" placeholder="" required v-model="start">
                <small class="invalid-feedback fw-bold">Start date is required!</small>
            </div>
        </div>
        <div class="col-12 col-md-6">
            <div class="form-group">
                <label for="end-date" class="fw-bold">End Date</label>
                <input type="date" class="form-control" name="end-date" id="end-date" placeholder="" required v-model="end">
                <small class="invalid-feedback fw-bold">End date is required!</small>
            </div>
        </div>
        <div class="form-group">
            <label for="participants" class="fw-bold">Participants</label>
            <input type="text" class="form-control" name="participants" id="participants" placeholder="Invite someone" v-model="participants">
        </div>
        <div class="col-12">
            <div class="form-group">
                <label for="content" class="fw-bold">Notes</label>
                <textarea name="content" id="content" cols="30" rows="3" class="form-control" placeholder="Notes" required v-model="content"></textarea>
                <small class="invalid-feedback fw-bold">This field is required!</small>
            </div>
        </div>
        <div class="col-12 d-flex align-items-center justify-content-between">
            <label class="form-check-label text-start fw-bold ms-0" for="reminder">Set Reminder</label>
            <div class="form-check form-switch">
                <input class="form-check-input ms-auto" type="checkbox" role="switch" id="reminder" v-model="reminder">
            </div>
        </div>
        <button type="submit" class="btn btn-dark btn-lg w-100 rounded-pill fw-bold shadow-sm">
            Create task
        </button>
    </form>
</template>

<script>
    export default {
        name: 'AddTask',
        data(){
            return{
                id: Math.round(Math.random() * 10000),
                title: '',
                category: [],
                background: '',
                content: '',
                participants: [],
                location: '',
                allDay: false,
                start: new Date(),
                end: new Date(),
                reminder: false
            }
        },
        methods: {
            addTask(e){
                e.preventDefault();
                const newTask = {
                    id: this.id,
                    title: this.title,
                    category: this.category,
                    background: this.background,
                    content: this.content,
                    participants: this.participants,
                    location: this.location,
                    allDay: false,
                    start: this.start,
                    end: this.end,
                    reminder: this.reminder
                }
                this.$emit('add-task', newTask);
                this.id = Math.round(Math.random() * 10000);
                this.title = '';
                this.category = ''
                this.background = '';
                this.content = '';
                this.participants = '';
                this.location = '';
                this.allDay = false;
                this.start = new Date();
                this.end = new Date();
                this.reminder = false;
            }
        },
        emits: ['add-task']
    }
</script>