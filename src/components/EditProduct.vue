<template>
  <div>
    <h2>Edit Product</h2>
    <form @submit.prevent="updateProduct">
      <div class="form-group">
        <label for="name">Name</label>
        <input type="text" id="name" v-model="name" required />
      </div>
      <div class="form-group">
        <label for="description">Description</label>
        <textarea
          id="description"
          rows="4"
          v-model="description"
          required
        ></textarea>
      </div>
      <div class="form-group">
        <label for="price">Price</label>
        <input
          type="number"
          id="price"
          min="0"
          step="0.01"
          v-model="price"
          required
        />
      </div>
      <button type="Modify Product">Update Product</button>
    </form>
  </div>
</template>

<script>
export default {
  props: ["product"],
  created() {
    this.editProduct = JSON.parse(this.product);
    this.name = this.editProduct["name"];
    this.description = this.editProduct["description"];
    this.price = this.editProduct["price"];
  },
  data() {
    return {
      editProduct: [],
      name: "",
      description: "",
      price: "",
    };
  },
  methods: {
    updateProduct() {
      this.editProduct = {
        id: this.editProduct.id,
        name: this.name,
        description: this.description,
        price: this.price,
      };
      this.$emit("editProduct", this.editProduct);
      this.$router.push("/");
    },
  },
};
</script>

<style scoped>
.form-group {
  margin-bottom: 15px;
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
</style>
