<template>
  <div class="products-index">
    <h1>All Products</h1>
    <div v-for="product in products" v-bind:key="product.id">
      <h4>{{ product.name }}</h4>
      <p>description: {{ product.description }}</p>
      <router-link :to="`/product/${product.id}`">See Details</router-link>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      products: [],
    };
  },
  created: function () {
    axios.get("/products").then((response) => {
      console.log(response.data);
      this.products = response.data;
    });
  },
  methods: {},
};
</script>
