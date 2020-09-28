<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <ProductAdd @add:product="addProduct" />
    <ProductList
      @delete:product="deleteProduct"
      @update:product="updateProduct"
      :products="products"
    />
  </div>

  
</template>


<script>
import ProductList from "./components/ProductList";
import ProductAdd from "./components/ProductAdd";
export default {
  name: "App",
  components: {
    ProductList,
    ProductAdd,
  },
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    this.getProducts();
  },
  methods: {
    async getProducts() {
      const result = await fetch(
        "https://jsonplaceholder.typicode.com/posts/1/comments"
      );
      const data = await result.json();
      this.products = data;
    },
    deleteProduct(product) {
      this.products = this.products.filter(
        (productToFilter) => productToFilter.id !== product.id
      );
    },
    updateProduct() {},
    addProduct(product) {
      const newProduct = { ...product };
      this.products = [...this.products, newProduct];
    },
  },
};
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
</style>
