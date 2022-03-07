<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
  @import '@/scss/index.scss';

  *{
    @include all;
    font-family: var(--my-font-family);
  }

  html{
    background-color: $bg-color; 
    color: $text-color;
  }

  #app {
    width: 100%;
    height: 100%;
  }
</style>