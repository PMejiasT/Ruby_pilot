<template>
  <div>
    <h1 class="textWeb titleG">Inicio</h1>
    <div class="imagenRuby"></div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {};
  },
};
</script>

<style lang="scss">
.imagenRuby{
  display:inline-block;
  width:100%;
  height:calc(100vh - 50px - 40px);
  box-sizing:border-box;
  position:relative;
  background-image: url("~/assets/img/pokemon-ruby.png");
  background-repeat: no-repeat;
  background-size: 100%;
}
.column, .blind, .blindImg{
  position:absolute;
  top:0;
  height:100%;
  box-sizing:border-box;
}

.blind{
  overflow:hidden;
}

.blindImg{
  width:100%;
  background-size:cover;
}
</style>
