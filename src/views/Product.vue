<template>
  <b-container>
    <b-row>
      <ProductCard
        v-for="product in products"
        :key="'product-' + product.id"
        :product="product"
        @add-item-to-cart="addItemToCart"
      />
    </b-row>
  </b-container>
</template>

<script>
import ProductCard from "../components/product/ProductCard.vue";

export default {
  name: "Product",
  components: {
    ProductCard,
  },
  data() {
    return {
      products: [
        {
          id: 1,
          price: 100,
          name: "Shoes 1",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",

          quantity: 1,
          star: 3,
          defaultColorId: 1,
          defaultSizeId: 1,
          images: [
            {
              id: 1,
              color: "#ba7e7e",
              img: require("@/assets/shoes_pink.png"),
            },
            {
              id: 2,
              color: "blue",
              img: require("@/assets/shoes_blue.png"),
            },
          ],
          sizes: [
            {
              id: 1,
              name: 5,
              price: 100,
            },
            {
              id: 2,
              name: 6,
              price: 105,
            },
            {
              id: 3,
              name: 7,
              price: 110,
            },
            {
              id: 4,
              name: 8,
              price: 115,
            },
            {
              id: 5,
              name: 9,
              price: 120,
            },
            {
              id: 6,
              name: 10,
              price: 125,
            },
            {
              id: 7,
              name: 11,
              price: 130,
            },
          ],
        },
        {
          id: 2,
          price: 200,
          name: "Shoes 2",
          star: 4,
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",

          quantity: 1,
          defaultColorId: 2,
          defaultSizeId: 3,
          images: [
            {
              id: 1,
              color: "#ba7e7e",
              img: require("@/assets/shoes_pink.png"),
            },
            {
              id: 2,
              color: "blue",
              img: require("@/assets/shoes_blue.png"),
            },
          ],
          sizes: [
            {
              id: 1,
              name: 5,
              price: 100,
            },
            {
              id: 2,
              name: 6,
              price: 105,
            },
            {
              id: 3,
              name: 7,
              price: 110,
            },
            {
              id: 4,
              name: 8,
              price: 115,
            },
            {
              id: 5,
              name: 9,
              price: 120,
            },
            {
              id: 6,
              name: 10,
              price: 125,
            },
            {
              id: 7,
              name: 11,
              price: 130,
            },
          ],
        },
        {
          id: 3,
          price: 300,
          star: 1,

          name: "Shoes 3",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",

          quantity: 1,
          defaultColorId: 1,
          defaultSizeId: 1,
          images: [
            {
              id: 1,
              color: "#ba7e7e",
              img: require("@/assets/shoes_pink.png"),
            },
            {
              id: 2,
              color: "blue",
              img: require("@/assets/shoes_blue.png"),
            },

            {
              id: 4,
              color: "gray",
              img: require("@/assets/shoes_gray.png"),
            },
          ],
          sizes: [
            {
              id: 1,
              name: 5,
              price: 100,
            },
            {
              id: 2,
              name: 6,
              price: 105,
            },
            {
              id: 3,
              name: 7,
              price: 110,
            },
            {
              id: 4,
              name: 8,
              price: 115,
            },
            {
              id: 5,
              name: 9,
              price: 120,
            },
            {
              id: 6,
              name: 10,
              price: 125,
            },
            {
              id: 7,
              name: 11,
              price: 130,
            },
          ],
        },
        {
          id: 4,
          price: 400,
          name: "Shoes 4",
          description:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
          quantity: 1,
          defaultColorId: 1,
          star: 5,
          defaultSizeId: 1,
          images: [
            {
              id: 1,
              color: "#ba7e7e",
              img: require("@/assets/shoes_pink.png"),
            },
            {
              id: 2,
              color: "blue",
              img: require("@/assets/shoes_blue.png"),
            },

            {
              id: 3,
              color: "green",
              img: require("@/assets/shoes_green.png"),
            },
          ],
          sizes: [
            {
              id: 1,
              name: 5,
              price: 100,
            },
            {
              id: 2,
              name: 6,
              price: 105,
            },
            {
              id: 3,
              name: 7,
              price: 110,
            },
            {
              id: 4,
              name: 8,
              price: 115,
            },
            {
              id: 5,
              name: 9,
              price: 120,
            },
            {
              id: 6,
              name: 10,
              price: 125,
            },
            {
              id: 7,
              name: 11,
              price: 130,
            },
          ],
        },
      ],
    };
  },

  methods: {
    addItemToCart({product,quantity}) { // Pass the params to App.vue
      console.log("product");
      this.$emit("add-item-to-cart", {
        product: product,
        quantity: quantity,
      });
    },
  },
};
</script>

<style></style>
