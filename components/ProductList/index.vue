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
  margin-top: 2rem;
  margin-bottom: 5rem;

  @media only screen and (min-width: 360px) {
    width: 100%;
  }

  @media only screen and (min-width: 640px) {
    width: 69%;
  }

  @media only screen and (min-width: 910px) {
    width: 65%;
  }

  @media only screen and (min-width: 1080px) {
    width: 68%;
  }

  @media only screen and (min-width: 1360px) {
    width: 62%;
  }

  @media only screen and (min-width: 1780px) {
    width: 60%;
  }

}

.cardsContainer {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;

  @media only screen and (min-width: 360px) {
    justify-content: center;
  }

  @media only screen and (min-width: 1080px) {
    justify-content: space-between; 
  }
 
}
</style>
