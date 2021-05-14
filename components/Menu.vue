<template>
  <div class="menu">
    <div class="item"><NuxtLink to="/">Inicio</NuxtLink></div>
    <div class="item"><NuxtLink to="/offers">Ofertas</NuxtLink></div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
export default Vue.extend({
  name: 'Menu',
});
</script>

<style lang="scss">
.menu {
  display: flex;
  align-items: center;
  align-content: center;
  min-height: 45px;
}
.menu .item {
  line-height: 25px;
  background-color: $app-main-color;
  margin: 5px;
  padding: 5px;
  cursor: pointer;
}
.menu .item:hover {
  background-color: $app-main-hover-color;
}
@media (max-width: $breakpoint-md) {
  .hide-small {
    display: none;
  }
  .menu {
    display: block;
  }
  .menu .item {
    line-height: 25px;
    background-color: #cfd638;
    margin: 10px auto;
    padding: 10px;
    width: 50%;
    text-align: center;
  }
}
</style>