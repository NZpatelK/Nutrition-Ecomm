<template>
  <section class="prodSection">
    <div class="productsContainer">
      <div v-for="(prodData, index) in productsData.products" :key="index">
        <ProductCard :prodProp="prodData" />
      </div>
    </div>
  </section>
</template>

<script>
import productsData from '../data/bulletproofProduct.json'
import ProductCard from '../components/ProductCard.vue'
export default {
  components: {
    ProductCard
  },
  data() {
    return {
      productsData: productsData
    }
  }
}
</script>

<style>
.prodSection {
  padding: 50px;
  margin: 50px;
}

.prodSection .productsContainer {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(330px, 1fr));
  grid-gap: 20px;
  width: 100%;
}
</style>
