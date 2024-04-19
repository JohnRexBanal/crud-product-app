<template>
<<<<<<< HEAD
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
        price: '',
=======
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
      <button type="submit" class="add-product-btn">Add Product</button>
      <div class="button-group">
        <router-link to="/" class="back-btn">Back</router-link>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      description: '',
      price: ''
    };
  },
  methods: {
    addProduct() {
      const product = {
        id: Date.now(),
        name: this.name,
        description: this.description,
        price: parseFloat(this.price)
>>>>>>> 045599554c119d777a73c8ac3022ace818da4f05
      };
      this.$emit('addProduct', product);
      this.$router.push('/');
    }
  }
};
</script>

<style scoped>
.add-product-btn {
  background-color: #28a745;
  color: #fff;
  padding: 8px 15px;
  font-size: 0.9rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-product-btn:hover {
  background-color: #218838;
}

.button-group {
  margin-top: 10px;
}

.back-btn {
  display: inline-block;
  color: #007bff;
  text-decoration: none;
  padding: 5px 10px;
  border: 1px solid #007bff;
  border-radius: 4px;
  transition: background-color 0.3s, color 0.3s;
}

.back-btn:hover {
  background-color: #007bff;
  color: #fff;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

button.add-product {
  background-color: #28a745;
  padding: 8px 15px;
  font-size: 0.9rem;
}

button.add-product:hover {
  background-color: #218838;
}
</style>