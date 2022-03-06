<template>
  <div class="home">
    <BiDarkMode/>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import BiDarkMode from '@/components/generic_components/bi-dark_mode.vue';

export default Vue.extend({
  name: 'Home',
  components: {
    BiDarkMode
  },
});
</script>