<template>
  <div class="v-catalog">
    <h1>Catalog</h1>
    <div class="v-catalog_list">
    <v-catalog-item
      v-for="product in PRODUCTS"
      :key="product.article"
      :product_data="product"
      @sendArticle="showChildArticleInConsole"
    />
    </div>
  </div>
</template>

<script>
import vCatalogItem from './v-catalog-item'
import {mapActions, mapGetters} from 'vuex'
export default {
  name: "v-catalog",
  components: {
    vCatalogItem,
  },
  props: {},
  data() {
    return {
      // products: [
      //   {
      //     image: "1.jpg",
      //     name: "T-shirt 1",
      //     price: "100",
      //     article: "T1",
      //     available: true
      //   },
      //   {
      //     image: "2.jpg",
      //     name: "T-shirt 2",
      //     price: "120",
      //     article: "T2",
      //     available: true
      //   },
      //   {
      //     image: "3.jpg",
      //     name: "T-shirt 3",
      //     price: "150",
      //     article: "T3",
      //     available: true
      //   },
      //   {
      //     image: "4.jpg",
      //     name: "T-shirt 4",
      //     price: "130",
      //     article: "T4",
      //     available: true
      //   },
      //   {
      //     image: "5.jpg",
      //     name: "T-shirt 5",
      //     price: "170",
      //     article: "T5",
      //     available: true
      //   },
      //   {
      //     image: "6.jpg",
      //     name: "T-shirt 6",
      //     price: "180",
      //     article: "T6",
      //     available: true
      //   }
      // ]
    }
  },
  computed: {
    ...mapGetters([
        'PRODUCTS'
    ]),
  },
  methods: {
    ...mapActions([
        'GET_PRODUCTS_FROM_API'
    ]),
    showChildArticleInConsole(data) {
      console.log(data)
    },
    mounted() {
      this.GET_PRODUCTS_FROM_API()
      .then((response) => {
        if (response.data){
          console.log('data arrived')
        }
      })
    }
  }
}
</script>

<style lang="scss">
  .v-catalog {
      &_list {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;
      }
  }
</style>