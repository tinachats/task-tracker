<template>
  <div class="container-fluid">
    <div class="row align-items-md-start gx-3 py-2">
       <SideMenu />
       <MainContent />
    </div>
  </div>
</template>

<script>
   import SideMenu from './components/SideMenu.vue';
   import MainContent from './components/MainContent.vue';
   import RightSection from './components/RightSection.vue';

   export default{
      components: {
        SideMenu,
        MainContent,
        RightSection,
      }
    }
</script>
