<template>
  <div class="container col-4 mt-3">
    <div class="images">
      <img height="200" :src="image" />
    </div>
    <Sizes
      :sizes="product.sizes"
      :defaultSize="product.defaultSizeId"
      :selectSize="selectSize"
    />
    <Colors
      :images="product.images"
      :defaultColor="product.defaultSizeId"
      :selectColor="selectColor"
    />

    <div class="product">
      <h1>{{ product.name }}</h1>
      <h2 :style="{ color }">${{ price }}</h2>
      <p class="desc">
        {{ product.description }}
      </p>
      <Stars :value="product.star" />

      <div class="row">
        <div class="buttons col">
          <QuantitySelect :size="10" @update-quantity="updateQuantity" />
          <button
            @click="addToCart(product)"
            :style="{
              backgroundColor: color,
            }"
          >
            Add to Cart
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Stars from "./Stars.vue";
import QuantitySelect from "./QuantitySelectBox.vue";
import Sizes from "./Sizes.vue";
import Colors from "./Colors.vue";

export default {
  name: "ProductCard",
  props: {
    product: Object,
  },
  components: {
    Stars,
    QuantitySelect,
    Sizes,
    Colors,
  },

  data() {
    return {
      quantity: 1,
    };
  },

  computed: {
    price() {
      return this.product.sizes.find(
        (size) => size.id === this.product.defaultSizeId
      ).price;
    },
    image() {
      return this.product.images.find(
        (img) => img.id === this.product.defaultColorId
      ).img;
    },
    color() {
      return this.product.images.find(
        (img) => img.id === this.product.defaultColorId
      ).color;
    },
  },

  methods: {
 
    addToCart(product) {
      this.$emit("add-item-to-cart", { product, quantity: this.quantity }); //Sent product and quantity to Product.vue
      this.$toast.success(`${product.name} is added to cart`);
    },


    selectColor(img) {
      this.product.defaultColorId = img.id;
    },

    selectSize(size) {
      this.product.defaultSizeId = size.id;
    },

    /***
     * @param {Number} quantity
     */
    updateQuantity(quantity) {
      this.quantity = quantity;
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Lato:400,700");

.lighter-text {
  color: #abb0be;
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
  position: relative;
  margin: auto;
  overflow: hidden;
  width: 520px;
  height: 350px;
  background: #f5f5f5;
  box-shadow: 5px 5px 15px #95afc0;
  border-radius: 10px;
}
p {
  font-size: 0.6em;
  color: #95afc0;
  letter-spacing: 1px;
}
h1 {
  font-size: 1.2em;
  color: #95afc0;
  margin-top: -5px;
}
h2 {
  color: #95afc0;
  margin-top: -5px;
}
img {
  width: 290px;
  margin-top: 47px;
}

.product {
  position: absolute;
  width: 40%;
  height: 100%;
  top: 10%;
  left: 60%;
}
.desc {
  text-transform: none;
  letter-spacing: 0;
  margin-bottom: 17px;
  color: #4e4e4e;
  font-size: 0.7em;
  line-height: 1.6em;
  margin-right: 25px;
  text-align: justify;
}
button {
  background: #95afc0;
  padding: 10px;
  display: inline-block;
  outline: 0;
  border: 0;
  margin: -1px;
  border-radius: 2px;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: #f5f5f5;
  cursor: pointer;
}
button:hover {
  background: #95afc0;
  transition: all 0.4s ease-in-out;
}
</style>
