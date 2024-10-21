<template>
    <div class="product-item">
      <img :src="require('@/assets/images/' + product.imagen)">
      <center>
        <h3>{{ product.nombre }}</h3>
        <h2> <b>$ {{ product.precio }}</b></h2>
        <button @click="addToCart">Agregar al carrito</button>
      </center>
    </div>
  </template>
  
  <script>
  export default {
    props: ['product'],
    methods: {
      addToCart() {
        this.$emit('addToCart', this.product);
      }
    }
  };
  </script>
  
  <style scoped>
  .product-item {
    border: 1px solid #ccc;
    padding: 10px;
    width: 200px;
  }
  img {
  margin: 10px;
  width: 200px;
  height: 200px;
  border: 5px solid purple;
  }
  h3, h2, button {
    margin: 5px;
  }
  button {
    background-color: purple;
    color: white;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
  }
  </style>
  
  