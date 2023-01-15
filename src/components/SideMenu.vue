<template>
    <div class="col-12 col-md-3 d-none d-xl-block">
        <div class="d-flex align-items-start">
            <div class="nav flex-column nav-pills me-3" id="v-pills-tab" role="tablist" aria-orientation="vertical">
                <button class="nav-link active" id="v-pills-dashboard-tab" data-bs-toggle="pill" data-bs-target="#v-pills-dashboard" type="button" role="tab" aria-controls="v-pills-dashboard" aria-selected="true">
                <div class="d-flex align-items-center justify-content-start">
                    <i class="bi-ui-checks-grid me-1"></i> Dashboard
                </div>
                </button>
                <button class="nav-link" id="v-pills-analytics-tab" data-bs-toggle="pill" data-bs-target="#v-pills-analytics" type="button" role="tab" aria-controls="v-pills-analytics" aria-selected="false">
                    <div class="d-flex align-items-center justify-content-start">
                    <i class="bi-pie-chart-fill me-1"></i> Analytics
                </div>
                </button>
                <button class="nav-link" id="v-pills-documents-tab" data-bs-toggle="pill" data-bs-target="#v-pills-teams" type="button" role="tab" aria-controls="v-pills-teams" aria-selected="false">
                    <div class="d-flex align-items-center justify-content-start">
                    <i class="bi-people me-1"></i> Teams
                </div>
                </button>
                <button class="nav-link" id="v-pills-documents-tab" data-bs-toggle="pill" data-bs-target="#v-pills-documents" type="button" role="tab" aria-controls="v-pills-documents" aria-selected="false">
                    <div class="d-flex align-items-center justify-content-start">
                    <i class="bi-file-earmark-text me-1"></i> Documents
                </div>
                </button>
                <button class="nav-link" id="v-pills-settings-tab" data-bs-toggle="pill" data-bs-target="#v-pills-settings" type="button" role="tab" aria-controls="v-pills-settings" aria-selected="false">
                    <div class="d-flex align-items-center justify-content-start">
                    <i class="bi-gear me-1"></i> Settings
                </div>
                </button>
            </div>
        </div>
    </div>
</template>
<script>
  export default {
    name: 'SideMenu'
  }
</script>