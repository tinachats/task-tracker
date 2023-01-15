<template>
    <div class="col-12 col-md-6 col-xl-4">
        <Header />
        <AddTask />
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