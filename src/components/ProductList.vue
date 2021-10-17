<template>
  <ul>
    <ProductListEntry
      v-for="product in products"
      :key="product.id"
      v-bind="product"
    ></ProductListEntry>
  </ul>
</template>
<script>
import ProductListEntry from "@/components/ProductListEntry.vue";
export default {
  name: "ProductList",
  components: { ProductListEntry },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    async getProducts() {
      const url = "http://localhost:3000/products";
      const productsAPI = await fetch(url, {
        headers: {
          Accept: "application/json",
        },
        method: "GET",
      });
      this.products = await productsAPI.json();
    },
  },
  async created() {
    this.getProducts();
  },
};
</script>

<style lang="scss">
ul {
  list-style-type: none;
  padding: 0;
  display: grid;
  gap: 1rem;
}
</style>
