<template>
  <div class="home" id="home">
    <Navbar :routes="routes" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Navbar from "@/components/page_components/Navbar.vue";

export default Vue.extend({
  name: 'Home',
  components: {
    Navbar
  },
  data() {
    return {
      routes: [
        {
          name: 'Who Am I',
          iconName: 'account-circle-outline',
        },
        {
          name: 'Education',
          iconName: 'school-outline',
        },
        {
          name: 'Experience',
          iconName: 'briefcase-outline',
        },
        {
          name: 'Skills',
          iconName: 'code-tags',
        },
        {
          name: 'Projects',
          iconName: 'folder-outline',
        },
        {
          name: 'Contact',
          iconName: 'email-outline',
        },
      ]
    };
  }
});
</script>

<style lang="scss">
@import '@/scss/index.scss';

 .home{
   width: 100%;
   @include flex-container(column, stretch, flex-start, nowrap);
 }
</style>