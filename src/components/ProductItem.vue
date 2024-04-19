<!-- product list -->

<!-- product list -->

<template>
  <li @click="handleEdit(product)" class="product-item">
    <h3>{{ product.name }}</h3>
    <p>{{ product.description }}</p>
    <p>{{ product.price }}</p>
    <button @click.stop="deleteProduct(product)">Delete</button>
  </li>
</template>
  
  <script>
export default {
  props: ["product"],
  methods: {
    handleEdit(product) {
      this.$emit("editProduct", product);
    },
    deleteProduct() {
      this.$emit("deleteProduct", this.product);
    },
  },
};
</script>
  
  <style scoped>
  .product-item {
    cursor: pointer;
    padding: 10px;
    border: 1px solid #ccc;
    margin-bottom: 10px;
  }
  </style>
  