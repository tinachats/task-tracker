<template>
    <div class="col-12 col-md-5">
        <div class="tab-content" id="v-pills-tabContent">
            <div class="tab-pane fade show active" id="v-pills-dashboard" role="tabpanel" aria-labelledby="v-pills-dashboard-tab">
                <h6 class="lead text-muted mb-0">{{ greeting }}</h6> 
                <h4 class="fw-bold mt-0">You've got <br> 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
            <div class="tab-pane fade" id="v-pills-analytics" role="tabpanel" aria-labelledby="v-pills-analytics-tab">
                <h6 class="lead text-muted mb-0">Analytics</h6> 
        <h4 class="fw-bold mt-0">You've got <br> 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
            <div class="tab-pane fade" id="v-pills-teams" role="tabpanel" aria-labelledby="v-pills-teams-tab">
                <h6 class="lead text-muted mb-0">Teams</h6> 
        <h4 class="fw-bold mt-0">You've got <br> 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
            <div class="tab-pane fade" id="v-pills-documents" role="tabpanel" aria-labelledby="v-pills-documents-tab">
                <h6 class="lead text-muted mb-0">Documents</h6> 
        <h4 class="fw-bold mt-0">You've got <br> 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
            <div class="tab-pane fade" id="v-pills-settings" role="tabpanel" aria-labelledby="v-pills-settings-tab">
                <h6 class="lead text-muted mb-0">Settings</h6> 
                <h4 class="fw-bold mt-0">You've got <br> 8 tasks today <i class="bi-journal-text"></i></h4>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name: 'MainContent',
    data(){
        return{
            greeting: this.userGreeting()
        }
    },
    methods: {
        userGreeting(){
            const hr = new Date().getHours();
            if (hr < 12){
                this.greeting = 'Good morning!';
            } else if(hr < 18){
                this.greeting = 'Good afternoon!';
            } else if(hr < 21){
                this.greeting = 'Good evening';
            } else {
                this.greeting = 'Good night!';
            }
            return this.greeting;
        }
    }
}
</script>