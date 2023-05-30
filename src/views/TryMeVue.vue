<template>
  <div class="flex flex-col flex-1 items-center">
    <ProductCard />
  </div>
</template>

<script setup>
import axios from "axios";
import ProductCard from "../components/ProductCard.vue";

const options = {
  method: 'GET',
  url: 'https://fakestoreapi.com/products'
};

const getMovieList = async () => {
  try {
    const response = await axios.request(options);
    console.log(response.data);
  } catch (error) {
    console.error(error);
  }
}

const data = await getMovieList();
console.log(data);
</script>
<style lang="scss" scoped></style>