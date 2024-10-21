<!-- <template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Bienvenido a Ugly Dollss"/>
  <CatImages/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import CatImages from './components/CatImages.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    CatImages
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->


<template>
  <div id="app">
    <div id="nav">
      <HelloWorld msg="Bienvenido a Ugly Dollss" />
    </div>
    <ProductList @addToCart="addToCart" />
    <ShoppingCart :cart="cart" @removeFromCart="removeFromCart" />
  </div>
</template>

<script>

import HelloWorld from './components/HelloWorld.vue';
import ProductList from './components/ProductList.vue';
import ShoppingCart from './components/ShoppingCart.vue';

export default {
  components: { HelloWorld,ProductList, ShoppingCart },
  data() {
    return {
      cart: []
    };
  },
  methods: {
    addToCart(product) {
      var existItem = false;
      if (this.cart.some(item => item.clave === product.clave)) {
        product.cantidad++;
        existItem = true;
      }
      if (!existItem) {
        this.cart.push(product);
        product.cantidad = 1;        
      }
    },
    removeFromCart(index) {
      if (this.cart[index].cantidad >= 1) {
        this.cart[index].cantidad--;
      }
      if (this.cart[index].cantidad <= 0) {
        this.cart.splice(index, 1);        
      }
    },    
    envioPedido(msg) {
      const url = "https://api.whatsapp.com/api/send?phone=525554690638&text=" + msg;
      console.log(url);
      window.open(url, '_blank');
    }
  }
};
</script>

<style>
#app {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  background-color: pink;
  color: purple;
}
</style>

