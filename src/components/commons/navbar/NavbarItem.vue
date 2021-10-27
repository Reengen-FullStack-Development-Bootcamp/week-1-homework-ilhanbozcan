<template>
  <li
    
    class="clearfix"
  >
    <img
      :src="product.images.find((img) => img.id === product.defaultColorId).img"
      height="50"
      alt="item1"
    />
    <span class="item-name">{{ product.name }}</span>
    <span class="item-name">
      size :
      {{
        product.sizes.find((size) => size.id === product.defaultSizeId).name
      }}</span
    >

    <span class="item-price"
      >${{
        product.sizes.find((size) => size.id === product.defaultSizeId).price *
          product.quantity
      }}</span
    >
    <button @click="onDecrease(product)" class="btn btn-primary btn-sm">
      -
    </button>
    <span class="item-quantity btn-sm">{{ product.quantity }}</span>
    <button @click="onIncrease(product)" class="btn btn-warning btn-sm">
      +
    </button>
    <button @click="onRemove(product)" class="btn btn-danger btn-sm">
      X
    </button>
  </li>
</template>

<script>
export default {
  name: "CartItem",
  props: {
    product: Object,
    onDecrease: Function,
    onIncrease: Function,
    onRemove: Function,
  },
};
</script>

<style scoped>

.shopping-cart .shopping-cart-items {
  padding-top: 20px;
}
.shopping-cart .shopping-cart-items li {
  margin-bottom: 18px;
}
.shopping-cart .shopping-cart-items img {
  float: left;
  margin-right: 12px;
}
.shopping-cart .shopping-cart-items .item-name {
  display: block;
  padding-top: 10px;
  font-size: 16px;
}
.shopping-cart .shopping-cart-items .item-price {
  color: #6394f8;
  padding-left: 28%;
  margin-right: 5px;
}
.shopping-cart .shopping-cart-items .item-quantity {
  color: #abb0be;
}

.clearfix:after {
  content: "";
  display: table;
  clear: both;
}
</style>
