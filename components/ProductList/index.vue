<template>
  <div class="container">
    <div class="cardsContainer" v-if="productsList.length !== 0">
      <Card
        v-for="product in productsList"
        :key="product.id"
        :product="product"
        @addProduct="addProductToCart"
      />
    </div>
  </div>
</template>

<script>
import Card from "./Card/index.vue";
import { dataApi } from "../../services/dataApi";

export default {
  name: "ProductList",

  components: {
    Card,
  },

  data() {
    return {
      productsList: [],

      cart: [],
    };
  },

  watch: {
    cart: {
      handler(newValue) {
        localStorage.setItem("cart", JSON.stringify(newValue));
      },
      deep: true,
    },
    totalQuantity: (value) => {
      localStorage.setItem("cartItemsQty", value);
    },
  },

  computed: {
    totalQuantity() {
      return this.cart.reduce((total, product) => total + 1, 0);
    },
  },

  methods: {
    async asyncData() {
      try {
        const response = await dataApi.get(
          "https://raw.githubusercontent.com/owInteractive/desafio-frontend-2020/master/produtos.json"
        );
        this.productsList = response.data;
      } catch (error) {
        this.productsList = [];
      }
    },

    addProductToCart(product) {
      const index = this.cart.findIndex((p) => p.id === product.id);

      if (index === -1) {
        this.cart.push({ ...product, quantity: 1 });
      } else {
        this.cart[index].quantity += 1;
      }
    },
  
  },

  mounted() {
    this.asyncData();
    // const cartData = localStorage.getItem("cart");
    this.cart = JSON.parse(localStorage.getItem("cart")) || [];
  },
};
</script>

<style lang="scss" scoped>
.container {
  height: 100%;
  width: 60%;
  margin-top: 5rem;
  margin-bottom: 5rem;

  h1 {
    color: #444141;
  }
}

.cardsContainer {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
}
</style>
