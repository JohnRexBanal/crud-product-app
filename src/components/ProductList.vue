<template>
    <div>
      <h2>Product List</h2>
      <ul>
        <transition-group name="fade" tag="ul">
          <product-item
            v-for="product in products"
            :key="product.id"
            :product="product"
            @editProduct="editProduct(product)"
            @deleteProduct="deleteProduct(product)"
          ></product-item>
        </transition-group>
      </ul>
      <router-link to="/add" class="add-product-link">Add Product</router-link>
    </div>
  </template>
  
  <script>
  import ProductItem from '../components/ProductItem.vue';
  
  export default {
    components: {
      ProductItem
    },
    props: ['products'],
    methods: {
      //for updating product
      editProduct(product) {
        this.$router.push({ path: `/edit/${product.id}` });
      },
      //for deleteing product
      deleteProduct(product) {
        if (confirm('Are you sure you want to delete this product?')) {
          this.$emit('deleteProduct', product);
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  
  .add-product-link {
    padding: 8px 15px;
    background-color: #28a745;
    color: white;
    border-radius: 4px;
    text-decoration: none;
    transition: background-color 0.3s, transform 0.2s;
    font-size: 0.9rem;
    font-weight: 500;
    letter-spacing: 0.5px;
  }
  
  .add-product-link:hover {
    background-color: #218838;
  }
  </style>
  