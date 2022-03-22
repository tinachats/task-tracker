<template>
    <button @click="onClick" :style="{ background: btnColor }" class="btn btn-primary rounded-pill px-4">{{ btnText}}</button>
</template>

<script>
    export default{
        name: 'Button',
        props: {
            btnText: String,
            btnColor: String
        },
        methods: {
            onClick(){
                this.$emit('toggle-add-task')
            }
        }
    }
</script>