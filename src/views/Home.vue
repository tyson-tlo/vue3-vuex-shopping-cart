<template>
  <div class="home">
    <h1>Browse Our Selection</h1>
    <ProductDescriptionDrawer
      :product="product"
      :active="active"
      v-on:closeProductDrawer="closeProductDrawer()" />
    <div class="product-cards-container">
      <ProductSummaryCard
        v-for="(item, i) in items"
        :key="i"
        :product="item"
        v-on:view-product="viewProduct($event)" />
    </div>    
  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/items.js';
import ProductSummaryCard from '../components/products/ProductSummaryCard.vue'
import ProductDescriptionDrawer from '../components/products/ProductDescriptionDrawer.vue'

export default {
  name: "Home",
  components: {ProductSummaryCard,ProductDescriptionDrawer},
  data() {
    return {
      items: items,
      product: null,
      active: {
        product_drawer: false
      }
    }
  },
  methods: {
    viewProduct(product) {
      this.product = product
      this.active.product_drawer = true
    },
    closeProductDrawer() {
      this.active.product_drawer = false
    }
  }
};
</script>

<style lang="scss">
.product-cards-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
