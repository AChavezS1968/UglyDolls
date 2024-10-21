<template>
    <div>
      <center><h1>Catálogo de Productos</h1></center>      
      <div class="product-list">
        <ProductItem
          v-for="product in filteredProducts"
          :key="product.id"
          :product="product"
          @addToCart="addToCart"
        />
      </div>
    </div>
  </template>
  
  <script>
  import ProductItem from './ProductItem.vue';
  
  export default {
    components: { ProductItem },
    data() {
      return {
        products: [
          { id: 1, clave: '0001', nombre: 'Ojos', categoria: 'aretes', descripcion: 'Aretes de Ojos', imagen: '0001 Ojos.png' , precio: 35, cantidad: 0},
          { id: 2, clave: '0002', nombre: 'Caroline', categoria: 'aretes', descripcion: 'Aretes de Caroline', imagen: '0002 Caroline.png' , precio: 40, cantidad: 0},
          { id: 3, clave: '0003', nombre: 'Fantasmas', categoria: 'aretes', descripcion: 'Aretes de Fantasmas', imagen: '0003 Fantasmas.png' , precio: 45, cantidad: 0},
          { id: 4, clave: '0004', nombre: 'Murcielagos', categoria: 'aretes', descripcion: 'Aretes de Murcielagos', imagen: '0004 Murcielagos.png', precio: 50 , cantidad: 0},
          { id: 5, clave: '0005', nombre: 'Anillo Plateado', categoria: 'anillos', descripcion: 'Anillo elegante', imagen: '0001 Ojos.png' , precio: 55, cantidad: 0},
          { id: 6, clave: '0006', nombre: 'Tarjeta de Regalo', categoria: 'tarjetas', descripcion: 'Tarjeta de cumpleaños', imagen: '0001 Ojos.png', precio:60, cantidad: 0 },
          { id: 7, clave: '0007', nombre: 'Ojos', categoria: 'aretes', descripcion: 'Aretes de Ojos', imagen: '0001 Ojos.png' , precio: 35, cantidad: 0},
          { id: 8, clave: '0008', nombre: 'Caroline', categoria: 'aretes', descripcion: 'Aretes de Caroline', imagen: '0002 Caroline.png' , precio: 40, cantidad: 0},
          { id: 9, clave: '0009', nombre: 'Fantasmas', categoria: 'aretes', descripcion: 'Aretes de Fantasmas', imagen: '0003 Fantasmas.png' , precio: 45, cantidad: 0},
          { id: 10, clave: '0010', nombre: 'Murcielagos', categoria: 'aretes', descripcion: 'Aretes de Murcielagos', imagen: '0004 Murcielagos.png', precio: 50, cantidad: 0 },
          { id: 11, clave: '0011', nombre: 'Anillo Plateado', categoria: 'anillos', descripcion: 'Anillo elegante', imagen: '0001 Ojos.png' , precio: 55, cantidad: 0},
          { id: 12, clave: '0012', nombre: 'Tarjeta de Regalo', categoria: 'tarjetas', descripcion: 'Tarjeta de cumpleaños', imagen: '0001 Ojos.png', precio:60, cantidad: 0 },
          { id: 13, clave: '0013', nombre: 'Ojos', categoria: 'aretes', descripcion: 'Aretes de Ojos', imagen: '0001 Ojos.png' , precio: 35, cantidad: 0},
          { id: 14, clave: '0014', nombre: 'Caroline', categoria: 'aretes', descripcion: 'Aretes de Caroline', imagen: '0002 Caroline.png' , precio: 40, cantidad: 0},
          { id: 15, clave: '0015', nombre: 'Fantasmas', categoria: 'aretes', descripcion: 'Aretes de Fantasmas', imagen: '0003 Fantasmas.png' , precio: 45, cantidad: 0},
          { id: 16, clave: '0016', nombre: 'Murcielagos', categoria: 'aretes', descripcion: 'Aretes de Murcielagos', imagen: '0004 Murcielagos.png', precio: 50, cantidad: 0 },
          { id: 17, clave: '0017', nombre: 'Anillo Plateado', categoria: 'anillos', descripcion: 'Anillo elegante', imagen: '0001 Ojos.png' , precio: 55, cantidad: 0},
          { id: 18, clave: '0018', nombre: 'Tarjeta de Regalo', categoria: 'tarjetas', descripcion: 'Tarjeta de cumpleaños', imagen: '0001 Ojos.png', precio:60, cantidad: 0 },
          { id: 19, clave: '0019', nombre: 'Ojos', categoria: 'aretes', descripcion: 'Aretes de Ojos', imagen: '0001 Ojos.png' , precio: 35, cantidad: 0},
          { id: 20, clave: '0020', nombre: 'Caroline', categoria: 'aretes', descripcion: 'Aretes de Caroline', imagen: '0002 Caroline.png' , precio: 40, cantidad: 0},
          { id: 21, clave: '0021', nombre: 'Fantasmas', categoria: 'aretes', descripcion: 'Aretes de Fantasmas', imagen: '0003 Fantasmas.png' , precio: 45, cantidad: 0},
          { id: 22, clave: '0022', nombre: 'Murcielagos', categoria: 'aretes', descripcion: 'Aretes de Murcielagos', imagen: '0004 Murcielagos.png', precio: 50, cantidad: 0 },
          { id: 23, clave: '0023', nombre: 'Anillo Plateado', categoria: 'anillos', descripcion: 'Anillo elegante', imagen: '0001 Ojos.png' , precio: 55, cantidad: 0},
          { id: 24, clave: '0024', nombre: 'Tarjeta de Regalo', categoria: 'tarjetas', descripcion: 'Tarjeta de cumpleaños', imagen: '0001 Ojos.png', precio:60, cantidad: 0 },
          { id: 25, clave: '0025', nombre: 'Ojos', categoria: 'aretes', descripcion: 'Aretes de Ojos', imagen: '0001 Ojos.png' , precio: 35, cantidad: 0},
          { id: 26, clave: '0026', nombre: 'Caroline', categoria: 'aretes', descripcion: 'Aretes de Caroline', imagen: '0002 Caroline.png' , precio: 40, cantidad: 0},
          { id: 27, clave: '0027', nombre: 'Fantasmas', categoria: 'aretes', descripcion: 'Aretes de Fantasmas', imagen: '0003 Fantasmas.png' , precio: 45, cantidad: 0},
          { id: 28, clave: '0028', nombre: 'Murcielagos', categoria: 'aretes', descripcion: 'Aretes de Murcielagos', imagen: '0004 Murcielagos.png', precio: 50, cantidad: 0 },
          { id: 29, clave: '0029', nombre: 'Anillo Plateado', categoria: 'anillos', descripcion: 'Anillo elegante', imagen: '0001 Ojos.png' , precio: 55, cantidad: 0},
          { id: 30, clave: '0030', nombre: 'Tarjeta de Regalo', categoria: 'tarjetas', descripcion: 'Tarjeta de cumpleaños', imagen: '0001 Ojos.png', precio:60, cantidad: 0 },
          { id: 31, clave: '0031', nombre: 'Ojos', categoria: 'aretes', descripcion: 'Aretes de Ojos', imagen: '0001 Ojos.png' , precio: 35, cantidad: 0},
          { id: 32, clave: '0032', nombre: 'Caroline', categoria: 'aretes', descripcion: 'Aretes de Caroline', imagen: '0002 Caroline.png' , precio: 40, cantidad: 0},
          { id: 33, clave: '0033', nombre: 'Fantasmas', categoria: 'aretes', descripcion: 'Aretes de Fantasmas', imagen: '0003 Fantasmas.png' , precio: 45, cantidad: 0},
          { id: 34, clave: '0034', nombre: 'Murcielagos', categoria: 'aretes', descripcion: 'Aretes de Murcielagos', imagen: '0004 Murcielagos.png', precio: 50, cantidad: 0 },
          { id: 35, clave: '0035', nombre: 'Anillo Plateado', categoria: 'anillos', descripcion: 'Anillo elegante', imagen: '0001 Ojos.png' , precio: 55, cantidad: 0},
          { id: 38, clave: '0036', nombre: 'Tarjeta de Regalo', categoria: 'tarjetas', descripcion: 'Tarjeta de cumpleaños', imagen: '0001 Ojos.png', precio:60, cantidad: 0 }
        ],
        categoriaSeleccionada: 'todos',
      };
    },
    computed: {
      filteredProducts() {
        if (this.categoriaSeleccionada === 'todos') {
          return this.products;
        }
        return this.products.filter(product => product.categoria === this.categoriaSeleccionada);
      }
    },
    methods: {
      addToCart(product) {
        this.$emit('addToCart', product);
      }
    }
  };
  </script>
  
  <style scoped>
  .product-list {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }
  </style>
  