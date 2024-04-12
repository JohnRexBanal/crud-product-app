<template>
  <div id="app">
    <router-view :products="products" @addProduct="addProduct" @editProduct="editProduct" @deleteProduct="deleteProduct" @updateProduct="updateProduct"></router-view>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: []
    };
  },
  methods: {
    addProduct(product) {
      this.products.push(product);
    },
    editProduct(product) {
      const index = this.products.findIndex(p => p.id === product.id);
      if (index !== -1) {
        this.products[index] = { ...product };
      }
    },
    deleteProduct(product) {
      const index = this.products.findIndex(p => p.id === product.id);
      if (index !== -1) {
        this.products.splice(index, 1);
      }
    },
    updateProduct(editedProduct) {
      const index = this.products.findIndex(p => p.id === editedProduct.id);
      if (index !== -1) {
        this.products[index] = { ...editedProduct };
      }
    }
  }
};
</script>

<style>
#app {
  font-family: 'Arial', sans-serif;
  margin: 20px;
  background-color: #f4f4f4;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h2 {
  border-bottom: 2px solid #333;
  padding-bottom: 10px;
  color: #333;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 15px;
  padding: 15px;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: #fff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li:hover {
  background-color: #f9f9f9;
}

button {
  padding: 8px 15px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.2s;
  font-size: 0.9rem;
  font-weight: 500;
  letter-spacing: 0.5px;
}

button:hover {
  background-color: #0056b3;
  transform: scale(1.05);
}

button.delete {
  background-color: #dc3545;
}

button.delete:hover {
  background-color: #c82333;
}

form {
  margin-top: 20px;
}

label {
  display: block;
  margin-bottom: 8px;
  color: #333;
}

input[type="text"],
input[type="number"],
textarea {
  width: 100%;
  padding: 8px;
  margin-bottom: 15px;
  border-radius: 4px;
  border: 1px solid #ccc;
}

input[type="text"]:focus,
input[type="number"]:focus,
textarea:focus {
  outline: none;
  border-color: #007bff;
  box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
