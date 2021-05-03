<template>
  <div class="offer">
    <h2>{{ offer.fields.title }}</h2>
    <img :src="offer.fields.image.fields.file.url" style="width: 250px;">
    <div v-html="offerbody" />
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


