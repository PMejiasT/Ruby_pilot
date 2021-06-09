<template>
  <div id="app">
    <Topbar @togglenav="navOpen = !navOpen" />
    <Sidebar :open="navOpen" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Topbar from '~/components/Topbar';
import Sidebar from '~/components/Sidebar';

export default Vue.extend({
  name: 'Menu',
  data: () => {
    return {
      navOpen: false
    }
  },
  components: {
    Topbar,
    Sidebar
  }
});
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    padding: 0;
    font-size: 1rem;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
</style>