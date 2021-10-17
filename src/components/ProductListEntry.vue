<template>
  <li class="product-entry">
    <div class="product-image">
      <img
        src="https://picsum.photos/175/150"
        alt="product picture description lorem ipsum dolor"
        class="product-picture"
      />
    </div>
    <div class="product-informations">
      <h2 class="product-title">{{ title }}</h2>
      <p class="product-manufacturer">{{ manufacturer }}</p>
      <p class="product-description">{{ description }}</p>
    </div>
    <div class="product-buy-information">
      <p class="product-netto-price price">{{ netPrice }}</p>
      <p class="product-gross-price price">{{ grossPrice }}</p>
      <button class="add-to-cart-btn" id="addToCartBtn" :click="addToCart">
        Add to Cart
      </button>
    </div>
  </li>
</template>

<script>
export default {
  name: "ProductListEntry",
  props: {
    title: {
      type: String,
    },
    manufacturer: {
      type: String,
    },
    description: {
      type: String,
    },
    netPrice: {
      type: Number,
    },
    grossPrice: {
      type: Number,
    },
  },
};
</script>

<style scoped lang="scss">
.product-entry {
  display: grid;
  gap: 0.5rem;
  grid-template-columns: 1fr 2fr 1fr;
  border: 1px solid black;
  padding: 0.25rem 0rem;
}
.product-entry > div {
  min-height: 13rem;
}
.product-picture {
  margin: 0.5rem;
  width: 90%;
}
.product-informations > * {
  text-align: left;
  margin-left: 0.5rem;
  margin-right: 0.5rem;
}
.product-title {
  margin: 0.25rem;
}
.product-manufacturer {
  margin-top: 0.25rem;
}
.product-description {
  margin-top: 2rem;
}
.price {
  text-align: left;
  margin: 0;
  margin-bottom: 0.5rem;
}
.price::after {
  content: ",- EUR";
}
.product-gross-price::after {
  content: ",- EUR incl. VAT";
}
.add-to-cart-btn {
  width: 100%;
  padding: 0.5rem;
}
.product-buy-information {
  display: flex;
  flex-flow: column;
  margin: 0.5rem;
}
.product-gross-price {
  flex-grow: 1;
}
</style>
