<template>
    <div class="col-12 col-md-6 col-xl-5">
        <Header />
        <AddTask @add-task="$emit('add-task', newTask)"/>
    </div>
</template>

<script>
import AddTask from './AddTask.vue';
import Header from './Header.vue';

export default {
    name: 'RightSection',
    components: {
        AddTask,
        Header,
    }
}
</script>