<template>
  <div class="topbar">
    <div>
      <span @click="$emit('togglenav')">MENU</span>
    </div>
  </div>
</template>
<style lang="scss" scoped>
  .topbar {
    display: flex;
    justify-content: space-between;
    width: 100vw;
    height: 50px;
    padding: 10px 16px;
    background-color: #222;
    border-bottom: 1px solid #000;
    box-shadow: 0 2px 4px #666;
    color: #fefefe;

    .icon {
      cursor: pointer;
    }
  }
</style>