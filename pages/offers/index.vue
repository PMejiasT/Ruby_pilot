<template>
  <div>
    <h1 class="titleOffer">Offers</h1>
    <div class="offers">
      <div class="offerItem" v-for="offer in offers" :key="offer.sys.id">
        <Offer :offer="offer" :offerbody="printRichText(offer.fields.body)" />
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import { createClient } from '~/plugins/contentful.js'
import { documentToHtmlString } from '@contentful/rich-text-html-renderer';
import Offer from '~/components/Offer';

const client = createClient()
const richTextOptions = {
  renderNode: {
    'embedded-asset-block': (node) =>
      `<img class="img-fluid" src="${node.data.target.fields.file.url}" height="${node.data.target.fields.file.details.image.height}" width="${node.data.target.fields.file.details.image.width}" alt="${node.data.target.fields.description}" />`,
    'hyperlink': (node) => {
      if((node.data.uri).includes("player.vimeo.com/video")){
        return `<iframe title="Unique Title 001" src=${node.data.uri} width="500" height="350" frameBorder="0" allowFullScreen></iframe>`
      } else if((node.data.uri).includes("youtube.com/embed")) {
        return `<iframe title="Unique Title 002" src=${node.data.uri} width="500" height="350" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" frameBorder="0" allowFullScreen></iframe>`
      }
    }
  }
}

export default Vue.extend({
  name: 'Index',
  components: {
    Offer,
  },
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
  },
  methods: {
    printRichText(richText) {
      return documentToHtmlString(richText, richTextOptions)
    }
  }
})
</script>

<style>
.offers {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.offerItem {
  width: 30%;
  margin-top: 90px;
  margin-bottom: 20px;
}
.titleOffer {
    position: absolute;
    top: 50%; 
    right: 50%;
    transform: translate(50%,-50%);
    text-transform: uppercase;
    font-family: verdana;
    font-size: 12em;
    font-weight: 700;
    color: #f5f5f5;
    text-shadow: 1px 1px 1px #919191,
        1px 2px 1px #919191,
        1px 3px 1px #919191,
        1px 4px 1px #919191,
        1px 5px 1px #919191,
        1px 6px 1px #919191,
        1px 7px 1px #919191,
        1px 8px 1px #919191,
        1px 9px 1px #919191,
        1px 10px 1px #919191,
    1px 18px 6px rgba(16,16,16,0.4),
    1px 22px 10px rgba(16,16,16,0.2),
    1px 25px 35px rgba(16,16,16,0.2),
    1px 30px 60px rgba(16,16,16,0.4);
}

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
