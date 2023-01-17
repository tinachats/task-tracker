<template>
    <div class="col-12 col-md-9">
        <div class="tab-content" id="v-pills-tabContent">
            <div class="tab-pane fade show active" id="v-pills-dashboard" role="tabpanel" aria-labelledby="v-pills-dashboard-tab">
                <div class="row align-items-md-start gx-3">
                    <!-- Main Content -->
                    <div class="col-12 col-md-6 col-xl-7">
                        <div class="d-flex align-items-center" v-html="greeting"></div>
                        <h4 class="fw-bold mt-0">You've got {{ tasks.length == 1 ? '1 task' : `${tasks.length} tasks` }} today <i class="bi-journal-text"></i></h4>
                        <ul class="my-3">
                            <Tasks @delete-task="deleteTask" @toggle-reminder="toggleReminder" :tasks="tasks"/>
                        </ul>
                    </div>
                    <!-- /.Main Content -->

                    <!-- Right Section Content -->
                    <div class="col-12 col-md-6 col-xl-5">
                        <Header @toggle-add-task="toggleAddTask" :showAddTask="showAddTask"/>
                        <div v-if="showAddTask">
                            <AddTask @add-task="addTask"/>
                        </div>
                    </div>
                    <!-- /.Right Section Content -->
                </div>
            </div>
            <div class="tab-pane fade" id="v-pills-analytics" role="tabpanel" aria-labelledby="v-pills-analytics-tab">
                <h6 class="lead text-muted mb-0">Analytics</h6> 
                <h4 class="fw-bold mt-0">You've got 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
            <div class="tab-pane fade" id="v-pills-teams" role="tabpanel" aria-labelledby="v-pills-teams-tab">
                <h6 class="lead text-muted mb-0">Teams</h6> 
                <h4 class="fw-bold mt-0">You've got 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
            <div class="tab-pane fade" id="v-pills-documents" role="tabpanel" aria-labelledby="v-pills-documents-tab">
                <h6 class="lead text-muted mb-0">Documents</h6> 
                <h4 class="fw-bold mt-0">You've got 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
            <div class="tab-pane fade" id="v-pills-settings" role="tabpanel" aria-labelledby="v-pills-settings-tab">
                <h6 class="lead text-muted mb-0">Settings</h6> 
                <h4 class="fw-bold mt-0">You've got 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
        </div>
    </div>
</template>

<script>
import AddTask from './AddTask.vue';
import Header from './Header.vue';
import Tasks from './Tasks.vue';

export default{
    name: 'MainContent',
    components: {
        Header,
        AddTask,
        Tasks,
    },
    data(){
        return{
            greeting: this.userGreeting(),
            tasks: [],
            showAddTask: false,
        }
    },
    methods: {
        successAlert() {
            iziToast.show({
                title: 'Hey',
                message: 'What would you like to add?'
            });
        },
        questionAlert(title, question, lists, id){
            iziToast.question({
                timeout: false,
                close: false,
                overlay: true,
                displayMode: 'once',
                id: 'question',
                zindex: 999,
                title: title,
                message: question,
                position: 'center',
                buttons: [
                    ['<button class="btn btn-danger"><b>YES</b></button>', function (instance, toast) {
                        lists = lists.filter(list => list.id != id);
                        instance.hide({ transitionOut: 'fadeOut' }, toast, 'button');
            
                    }, true],
                    ['<button>NO</button>', function (instance, toast) {
                        instance.hide({ transitionOut: 'fadeOut' }, toast, 'button');
            
                    }],
                ],
                onClosing: function(instance, toast, closedBy){
                    console.info('Closing | closedBy: ' + closedBy);
                },
                onClosed: function(instance, toast, closedBy){
                    console.info('Closed | closedBy: ' + closedBy);
                }
            });
        },
        userGreeting(){
            const hr = new Date().getHours();
            var greetingText, icon;
            if (hr < 12){
                icon = 'sunrise.svg';
                greetingText = 'Good morning!';
            } else if(hr < 18){
                icon = 'clear-day.svg';
                greetingText = 'Good afternoon!';
            } else if(hr < 20){
                icon = 'sunset.svg';
                greetingText = 'Good evening';
            } else {
                icon = 'clear-night.svg';
                greetingText = 'Good night!';
            }
            let output = `
                <img src="../src/assets/greeting-icons/${icon}" height="30" width="30">
                <h6 class="lead text-muted my-0">${greetingText}</h6>
            `;
            return output;
        },
        toggleAddTask(){
            this.showAddTask = !this.showAddTask;
        },
        async addTask(task){
            const res = await fetch('http://localhost:5000/tasks', {
                method: 'post',
                headers: {
                    'Content-type': 'application/json'
                },
                body: JSON.stringify(task)
            });
            const data = await res.json();
            this.tasks = [...this.tasks, data];
        },
        async deleteTask(id){
            if(confirm('Are you sure you want to delete this task?')){
                const res = await fetch(`http://localhost:5000/tasks/${id}`, {
                    method: 'DELETE'
                });

                res.status === 200 ? (this.tasks = this.tasks.filter(task => task.id != id)) : alert('Error in deleting task.')
            }
        },
        async toggleReminder(id){
            const taskToToggle = await this.fetchTask(id);
            const updatedTask = {...taskToToggle, reminder: !taskToToggle.reminder};

            const res = await fetch(`http://localhost:5000/tasks/${id}`, {
                method: 'PUT',
                headers: {
                    'Content-type': 'application/json'
                },
                body: JSON.stringify(updatedTask)
            });

            const data = await res.json();

            this.tasks = this.tasks.map((task) => 
                task.id === id ? {...task, reminder: data.reminder} : task
            );
        },
        async fetchTasks(){
            const res = await fetch('http://localhost:5000/tasks');
            const data = await res.json();
            return data;
        },
        async fetchTask(id){
            const res = await fetch(`http://localhost:5000/tasks/${id}`);
            const data = await res.json();
            return data;
        }
    },
    async created(){
        this.tasks = await this.fetchTasks();
      }
}
</script>