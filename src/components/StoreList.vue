<template>
  <main class="container text-white">
    <div class="pt-6">The number of selected product is: {{ cart.length }}</div>
    <div class="pt-6 flex justify-around flex-wrap">
      <div v-for="product in productData" :key="product.id">
        <ProductCard :product="product" :cart="cart" @addProduct="addProduct"/>
      </div>
    </div>
    <p v-if="productData.length === 0">
      No locations added. To start tracking a location, search in
      the field above.
    </p>
  </main>
</template>

<script>
import axios from "axios";
import {defineComponent} from "vue";
import ProductCard from "./ProductCard.vue";


export default defineComponent({
  components: {ProductCard},
  data() {
    return {
      productData: [],
      cart: []
    };
  },
  async mounted() {
    this.productData = await this.getProductData();
  },
  methods: {
    async getProductData() {
      try {
        const response = await axios.get("https://fakestoreapi.com/products");

        return response.data;
      } catch (error) {
        console.log(error);
      }
    },
    addProduct(id) {
      console.log(id);
      this.cart.push(id);
    }
  }
});


</script>

<style lang="scss" scoped></style>