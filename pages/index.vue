<template>
  <div>
    <h1>Inicio</h1>
    <div class="imagenRuby">
      <img src="~/assets/img/pokemon-ruby.png" />
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
  width:800px;
  height:600px;
  box-sizing:border-box;
  margin-top:40px;
  position:relative;
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
