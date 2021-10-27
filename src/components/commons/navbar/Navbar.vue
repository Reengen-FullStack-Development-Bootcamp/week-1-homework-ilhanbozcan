<template>
  <div>
    <nav>
      <div class="container">
        <ul class="navbar-left">
          <li><a href="#">Products</a></li>
        </ul>
        <!--end navbar-left -->

        <ul class="navbar-right">
          <li>
            <a @click="toogleCart" href="#" id="cart"
              ><i class="fa fa-shopping-cart"></i> Cart
              <span class="badge">{{ totalQuantity }}</span></a
            >
          </li>
        </ul>
        <!--end navbar-right -->
      </div>
      <!--end container -->
    </nav>

    <div v-if="isShoppingCartOpen" class="container">
      <div class="shopping-cart">
        <div class="shopping-cart-header">
          <i class="fa fa-shopping-cart cart-icon"></i
          ><span class="badge">{{ totalQuantity }}</span>
          <div class="shopping-cart-total">
            <span class="lighter-text">Total:</span>
            <span class="main-color-text">${{ totalPrice }}</span>
          </div>
        </div>
        <!--end shopping-cart-header -->

        <ul
          v-if="shoppingCart.length"
          class="shopping-cart-items"
          style="list-style-type:none;"
        >
          <NavbarItem
            v-for="product in shoppingCart"
            :key="'cart-' + product.defaultColorId + '-' + product.id"
            :product="product"
            :onIncrease="increaseQuantity"
            :onDecrease="decreaseQuantity"
            :onRemove="removeProduct"

          />
        </ul>
        <h3 v-else>Cart is empty 😢</h3>
      </div>
      <!--end shopping-cart -->
    </div>
    <!--end container -->
  </div>
</template>

<script>
import NavbarItem from "./NavbarItem";
export default {
  name: "Navbar",
  props: {
    shoppingCart: Array,
  },
  components: {
    NavbarItem,
  },
  data() {
    return {
      isShoppingCartOpen: false,
    };
  },

  computed: {
    totalPrice() {
      return this.shoppingCart.reduce((total, p) => {
        return (
          total +
          p.sizes.find((size) => p.defaultSizeId === size.id).price * p.quantity
        );
      }, 0);
    },
    totalQuantity() {
      return this.shoppingCart.reduce((total, p) => {
        return total + p.quantity;
      }, 0);
    },
  },
  methods: {
    toogleCart() {
      this.isShoppingCartOpen = !this.isShoppingCartOpen;
    },

    /***
     * @param {Object} product
     */

    addItemToCart(product) {
      this.shoppingCart.push(product);
    },

    /***
     * @param {Object} product
     */

    removeProduct(product) {
      this.shoppingCart = this.shoppingCart.filter(
        //Find exact item in cart
        (p) =>
          p.id !== product.id ||
          p.defaultColorId !== product.defaultColorId ||
          p.defaultSizeId !== product.defaultSizeId
      );
      this.$toast.error(`${product.name} is deleted`);
      this.$emit("remove-from-cart", this.shoppingCart); // Emit the updated cart to app.vue, because app.vue don't know cart is updated
      //Second uption is removeProduct function can define in App.vue, then it passes as parameter to Navbar
    },

    /***
     * @param {Object} product
     */

    increaseQuantity(product) {
      this.shoppingCart.map((p) => {
        //Find exact item in cart
        if (
          p.id === product.id &&
          p.defaultColorId === product.defaultColorId &&
          p.defaultSizeId === product.defaultSizeId
        ) {
          product.quantity += 1;
        }
      });
    },

    /***
     * @param {Object} product
     */
    decreaseQuantity(product) {
      if (product.quantity == 1) {
        //If quantity is 1 continue
        return 0;
      }
      this.shoppingCart.map((p) => {
        //Find exact item in cart
        if (
          p.id === product.id &&
          p.defaultColorId === product.defaultColorId &&
          p.defaultSizeId === product.defaultSizeId
        ) {
          product.quantity -= 1;
        }
      });
    },
  },
};
</script>

<style scoped>
@import url(https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/css/font-awesome.min.css);

.lighter-text {
  color: #abb0be;
}
.main-color-text {
  color: #6394f8;
}
nav {
  padding: 20px 0 40px 0;
  background: #7d6b7d;
  font-size: 16px;
}
nav .navbar-left {
  float: left;
}
nav .navbar-right {
  float: right;
}
nav ul li {
  display: inline;
  padding-left: 20px;
}
nav ul li a {
  color: #e8e8e8;
  text-decoration: none;
}

.container {
  margin: auto;
  width: 80%;
}
.badge {
  background-color: #6394f8;
  border-radius: 10px;
  color: white;
  display: inline-block;
  font-size: 12px;
  line-height: 1;
  padding: 3px 7px;
  text-align: center;
  vertical-align: middle;
  white-space: nowrap;
}
.shopping-cart {
  margin: 20px 0;
  float: right;
  margin-left: 53%;
  background: white;
  width: 320px;
  position: absolute;
  border-radius: 3px;
  padding: 20px;
  z-index: 1;
}
.shopping-cart .shopping-cart-header {
  border-bottom: 1px solid #e8e8e8;
  padding-bottom: 15px;
}
.shopping-cart .shopping-cart-header .shopping-cart-total {
  float: right;
}

.shopping-cart:after {
  bottom: 100%;
  left: 89%;
  border: solid transparent;
  content: " ";
  height: 0;
  width: 0;
  position: absolute;
  pointer-events: none;
  border-bottom-color: white;
  border-width: 8px;
  margin-left: -8px;
}
.cart-icon {
  color: #515783;
  font-size: 24px;
  margin-right: 7px;
  float: left;
}
.button {
  background: #6394f8;
  color: white;
  text-align: center;
  padding: 12px;
  text-decoration: none;
  display: block;
  border-radius: 3px;
  font-size: 16px;
  margin: 25px 0 15px 0;
}
.button:hover {
  background: #729ef9;
}

</style>
