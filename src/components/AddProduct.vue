<template>
    <div>
      <h2>Add Product</h2>
      <form @submit.prevent="addProduct">
        <div>
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="name" required>
        </div>
        <div>
          <label for="description">Description:</label>
          <textarea id="description" v-model="description" required></textarea>
        </div>
        <div>
          <label for="price">Price:</label>
          <input type="number" id="price" v-model.number="price" required>
        </div>
        <button type="submit">Add Product</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        description: '',
        price: 0
      };
    },
    methods: {
      addProduct() {
        const product = {
          id: Date.now(),
          name: this.name,
          description: this.description,
          price: parseFloat(this.price)
        };
        this.$emit('addProduct', product);
        this.$router.push('/');
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
  button.add-product {
    background-color: #28a745;
    padding: 8px 15px; /* Updated padding for consistent button size */
    font-size: 0.9rem; /* Updated font size for consistent button text size */
  }
  
  button.add-product:hover {
    background-color: #218838;
  }
  
  </style>
  