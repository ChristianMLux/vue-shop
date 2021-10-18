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
      <button
        class="add-to-cart-btn"
        id="addToCartBtn"
        @click="$emit('addToCart')"
      >
        Add to Cart
      </button>
    </div>
  </li>
</template>

<script>
export default {
  name: "ProductListEntry",
  emits: ["addToCart"],
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
  padding: 0.25rem 0rem;
  box-shadow: rgba(0, 0, 0, 0.12) 0px 1px 3px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
  border-radius: 0.25rem;
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
  margin: 0.25rem 0;
}
.product-manufacturer {
  margin: 0;
}
.product-description {
  margin: 2rem 0;
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
button {
  background: #a3db33;
  border-radius: 0.25rem;
  opacity: 0.9;
  border: none;
  box-shadow: rgba(0, 0, 0, 0.12) 0px 1px 3px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
  outline: 0.5px rgba(0, 0, 0, 0.12) 0px 1px 3px,
    rgba(0, 0, 0, 0.24) 0px 1px 2px;
}
button:active {
  outline: 1px solid darkgreen;
}
button:active::after {
  margin-left: 1rem;
  content: "\2714";
}
@media screen and (max-width: 550px) {
  .product-entry {
    padding: 0;
    display: grid;
    justify-content: center;
    gap: 0.5rem;
    grid-template-columns: auto;
    box-shadow: rgba(0, 0, 0, 0.12) 0px 1px 3px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
    border-radius: 0.25rem;
  }
  .product-entry > div {
    min-height: 8rem;
  }
  .product-picture,
  .product-image {
    margin: 0;
    width: 100%;
    border-top-left-radius: 0.25rem;
    border-top-right-radius: 0.25rem;
  }
  .product-image {
    justify-content: center;
  }
  .product-informations {
    padding: 0.5rem;
    padding-right: 1rem;
  }
}
</style>
