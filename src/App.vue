<template>
  <div id="app">
    <Toast/>
    <Navbar :shoppingCart="shoppingCart" @remove-from-cart="removeFromCart" />
    <ProductPage @add-item-to-cart="addItemToCart" />
  </div>
</template>

<script>
import Product from "./views/Product.vue";
import Navbar from "./components/commons/navbar/Navbar.vue";
import Toast from "./components/commons/Toast.vue";

export default {
  name: "App",
  components: {
    Navbar,
    ProductPage: Product,
    Toast
  },
  data() {
    return {
      shoppingCart: [],
    };
  },
  methods: {
    addItemToCart({product,quantity}) {
      let isIn = false;
      console.log(this.shoppingCart)
      this.shoppingCart = this.shoppingCart.map((p) => {
        if (p.id === product.id && p.defaultColorId === product.defaultColorId && p.defaultSizeId === product.defaultSizeId) {
          p.quantity += parseInt(quantity);
          isIn = true;
        }
        return p;
      });
      if (!isIn) {
        this.shoppingCart.push({...product,quantity:parseInt(quantity)});
      }
            console.log(this.shoppingCart)
    },

    removeFromCart(shoppingCart){
      this.shoppingCart = shoppingCart
}
  },
};
</script>

<style>
#app {
  background-color: #ededed;
  height: 100%;
}

html,
body {
  height: 100%;
}
</style>
