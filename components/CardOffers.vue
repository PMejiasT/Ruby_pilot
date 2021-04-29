<template>
  <div>
    <div v-for="offer in offers" :key="offer.sys.id">
        {{ offer.fields.title }}
        <img :src="offer.fields.image.fields.file.url" style="width: 250px;">
        <p v-for="offertext in offer.fields.body.content" :key="offertext">
        {{ offertext.value }}
          </p>
    </div>
  </div>
</template>

<script>
import {createClient} from '~/plugins/contentful.js'
//import { documentToHtmlString } from '@contentful/rich-text-html-renderer';
const client = createClient()

export default {
  // `env` is available in the context object
  asyncData ({env}) {
    return Promise.all([
          // fetch all blog posts sorted by creation date
      client.getEntries({
        'content_type': env.CTF_OFFERS_TYPE_ID,
        order: '-sys.createdAt',
      })
    ]).then(([offers]) => {
      // return data that should be available
      // in the template
      return {
        offers: offers.items
      }
    }).catch(console.error)
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

