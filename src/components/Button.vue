<template>
    <button @click="toggleAddTask" :class="`btn ${btnType} rounded-pill`">
        <div class="d-flex align-items-center justify-content-center fw-bold">
            <i :class="`${btnIcon} me-2`"></i> {{ btnText }}
        </div>
    </button>
</template>

<script>
   export default{
    name: 'Button',
    props: {
        btnText: String,
        btnType: String,
        btnIcon: String
    },
    methods: {
        toggleAddTask(){
            this.$emit('btn-click');
        }
    }
   }
</script>