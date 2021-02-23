<template>
  <div class="home">
    <h1>All Products</h1>
    <div class="row row-cols-1 row-cols-md-2">
      <div class="col mb-4" v-for="product in products" v-bind:key="product.id">
        <div class="card">
          <img v-bind:src="product.primary_image_url" class="card-img-top" alt="..." />
          <div class="card-body">
            <h5 class="card-title">{{ product.name }}</h5>
            <p class="card-text">{{ product.price }}</p>
            <a class="btn btn-primary" v-bind:href="`/products.${product.id}`">More Info</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.card-img-top {
  object-fit: cover;
  height: 350px;
}
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      products: [],
      name: "",
      formattedPrice: "",
      images: "",
    };
  },
  created: function() {
    this.indexProducts();
  },
  methods: {
    indexProducts: function() {
      axios.get("/api/products").then(response => {
        this.products = response.data;
        console.log("All Product:", this.products);
      });
    },
  },
};
</script>
