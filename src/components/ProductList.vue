<template>
  <ul>
    <ProductListEntry
      v-for="product in products"
      :key="product.id"
      @addToCart="addToCart(product)"
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
      userID: 12345,
      idx: 0,
    };
  },
  methods: {
    addToCart(product) {
      let cartItem = {
        productID: product.id,
        productTitle: product.title,
        buyerID: this.userID,
      };
      sessionStorage.setItem(this.idx, JSON.stringify(cartItem));
      this.idx++;
      var shoppingCart = [],
        keys = Object.keys(sessionStorage),
        i = keys.length;
      while (i--) {
        let item = JSON.parse(sessionStorage.getItem(keys[i]));
        shoppingCart.push(item);
      }
      console.log(shoppingCart);
    },
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
