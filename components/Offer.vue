<template>
  <div class="offer">
    <h2 class="titleOffer textWeb">{{ offer.fields.title }}</h2>
    <img class="imgOffer" :src="offer.fields.image.fields.file.url" style="width: 250px;">
    <div class="bodyOffer textWeb" v-html="offerbody" />
  </div>
</template>


<script>
import Vue from 'vue';

export default Vue.extend({
  name: 'Offer',
  props: {
    offer: {
      type: Object,
      required: true,
    },
    offerbody: {
      type: String,
      required: true
    }
  }
})
</script>

<style lang="scss">
.offer {
  margin-top: 90px;
  margin-bottom: 20px;
}
.titleOffer {
  font-size: 30px;
}
.imgOffer{
  cursor: pointer;
  border-radius: 20px;
}
.bodyOffer {
  font-size: 17x;
}
@media (max-width: 960px) and (min-width: 540px+1) {
  .offer {
    width: 45%;
  }
}
@media (max-width: 540px) {
  .offer {
    width: 100%;
  }
}
</style>
