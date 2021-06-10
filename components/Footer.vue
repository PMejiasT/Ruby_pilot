<template>
  <div class="footer">
    <p class="textWeb">Ruby</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
export default Vue.extend({
  name: 'Footer',
});
</script>

<style lang="scss">
.footer {
  background-color: #222;
  position: fixed;
  bottom: 0;
  width: 100%;
  height: 40px;
  color: white;
  text-align: center;
}
</style>