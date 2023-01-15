<template>
    <div class="col-12 col-md-6 col-xl-4">
        <div class="tab-content" id="v-pills-tabContent">
            <div class="tab-pane fade show active" id="v-pills-dashboard" role="tabpanel" aria-labelledby="v-pills-dashboard-tab">
                <div class="d-flex align-items-center" v-html="greeting"></div>
                <h4 class="fw-bold mt-0">You've got {{ tasks.length == 1 ? '1 task' : `${tasks.length} tasks` }} today <i class="bi-journal-text"></i></h4>
                <ul class="my-3">
                   <Tasks :tasks="tasks"/>
                </ul>
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
import Tasks from './Tasks.vue';

export default{
    name: 'MainContent',
    components: {
        Tasks,
    },
    data(){
        return{
            greeting: this.userGreeting(),
            tasks: []
        }
    },
    methods: {
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
        }
    },
    created(){
        this.tasks = [
            {
                id: 1,
                title: 'Football',
                category: 'sport',
                background: 'baige',
                content: 'Ligue 1 opener postponed after Marseille virus cases',
                participants: ['Emma', 'Liam'],
                location: 'Marlowe',
                start: '4:30 PM',
                end: '17:45 PM',
                reminder: false
            },
            {
                id: 2,
                title: 'Meeting',
                category: 'work',
                background: 'light_yellow',
                content: 'Approval of a new project',
                participants: ['Delroy'],
                location: 'Sightglass Coffee',
                start: '00:30 AM',
                end: '02:45 AM',
                reminder: true
            },
            {
                id: 3,
                title: 'English Lesson',
                category: 'school',
                background: 'sky_blue',
                content: '',
                participants: ['Emma', 'Liam', 'Tryson'],
                location: '270 7th St, San Francisco, CA',
                start: '08:15 AM',
                end: '10:45 AM',
                reminder: true
            },
            {
                id: 4,
                title: 'Make Prototypes',
                category: 'work',
                background: 'light_violet',
                content: 'Make and send prototypes to the client',
                participants: ['Tinashe', 'Kudzanai', 'Lizzie', 'Taurai'],
                location: 'work',
                start: '12:30 PM',
                end: '14:45 PM',
                reminder: true
            }
        ];
      }
}
</script>