<template>
  <div>
    <h2>{{ product.name }}</h2>
    <p>{{ product.price }}</p>
    <p>{{ product.description }}</p>
    <a v-bind:href="`/products/${product.id}/edit`">Edit This Post</a>
    <br />
    <a href="/products">Back to all Products</a>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      product: {},
    };
  },
  created: function() {
    this.showProducts();
  },
  methods: {
    showProduct: function() {
      axios.get("/api/products/" + this.$route.params.id).then(response => {
        console.log(response.data);
        this.product = response.data;
      });
    },
  },
};
</script>
