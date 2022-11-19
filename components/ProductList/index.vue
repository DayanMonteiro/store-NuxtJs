<template>
  <div class="container">
    <div class="cardsContainer" v-if="productsList.length !== 0">
      <Card
        v-for="product in productsList"
        :key="product.id"
        :product="product"
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

      products: [
      {
        id: 1,
        name: 'Product 1',
        description: 'This is an incredibly awesome product',
        quantity: 0,
      },
      {
        id: 2,
        name: 'Product 2',
        description: 'This is an incredibly awesome product',
        quantity: 0,
      },
      {
        id: 3,
        name: 'Product 3',
        description: 'This is an incredibly awesome product',
        quantity: 0,
      }
    ],
    showCart: false,


    cartData: [],
    };

  },

  computed: {
  cart() {
    cart = JSON.parse(localStorage.setItem('cart', [])); 
    return this.products.filter(product => product.quantity > 0);
  },
  totalQuantity() {
    return this.products.reduce(
      (total, product) => total + product.quantity,
      0
    );
  }
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

    updateCart(product, updateType) {      
    for (let i = 0; i < this.products.length; i++) {
      if (this.products[i].id === product.id) {
        if (updateType === 'subtract') {
          if (this.products[i].quantity !== 0) {
            this.products[i].quantity--;
            saveCart();
          }
        } else {
          this.products[i].quantity++;
          saveCart();
        }
        break;
      }
    }
  },

  saveCart(products) {
    localStorage.setItem('cart', JSON.stringify(products));
  }

  },

  mounted() {
    this.asyncData();

    const cartData = localStorage.getItem('cart');
  this.cartData = cartData ? JSON.parse(cartData) : [];
  },
};
</script>

<style lang="scss" scoped>
.container {
  // background-color: antiquewhite;
  height: 100%;
  width: 57%;
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

  background-color: aqua;

  flex-wrap: wrap;
}
</style>
