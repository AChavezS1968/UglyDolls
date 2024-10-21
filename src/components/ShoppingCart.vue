<template>
    <div class="shopping-cart">
      <center>
        <p v-if="cart.length === 0">Carrito de Compras Vacío</p>
        <p v-if="cart.length > 0">Carrito de Compras</p>
      </center>      
      <ul>
        <li v-for="(item, index) in cart" :key="index">
          {{ item.clave }} - {{ item.nombre }}   C: {{ item.cantidad }}
          <button @click="removeFromCart(index)"><img alt="delete" src="../assets/images/delete-button-png-32.png"></button>
        </li>
      </ul>
      <br>
      <h1>
      <p v-if="cart.length > 0">
          Total: {{ Number(cart.reduce((total, item) => total + item.precio * item.cantidad, 0)).toLocaleString('es-MX', { style: 'currency', currency: 'MXN' }) }}
      </p>
      </h1>
      <br>
      <center>
        <button class="btnCompra" v-if="cart.length > 0" @click="envioPedido">Realizar Compra</button>
      </center>      
    </div>
  </template>
  
  <script>

  export default {
    props: ['cart'],
    methods: {
      removeFromCart(index) {
        this.$emit('removeFromCart', index);
      },
      envioPedido() {
        const lines = this.cart.map(item => `${item.clave} - ${item.nombre} - Cantidad ${item.cantidad}`);
        const total = this.cart.reduce((total, item) => total + item.precio * item.cantidad, 0);
        const msg = `Favor de enviar el siguiente pedido:\n${lines.join("\n")}\nTotal: ${total.toLocaleString('es-MX', { style: 'currency', currency: 'MXN' })}`;

        this.$emit('envioPedido', msg);
      }
    }
  }
  </script>
  
  <style scoped>
  ul {
    list-style-type: none;
    padding: 0;
    width: 250px;
  }
  li {
    margin-bottom: 10px;
    height: 20px;
    width: 250px;
  }
  shopping-cart
  {
    border: 1px solid #ccc;
    padding: 10px;
    width: 250px;
  }
  img {
    background-color: transparent;
    margin: 1px;
    width: 10px;
    height: 10px;
  }
 .btnCompra {
    background-color: purple;
    color: white;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
  }
  </style>
  