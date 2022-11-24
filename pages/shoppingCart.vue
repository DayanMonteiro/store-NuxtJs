<template>
  <div>
      <Header />
    <div>
      <div class="containerTable">
        <Table :cartProducts="cartProducts" />
      </div>
      <div class="footerShoppingCartPage">
        <Footer />
      </div>
    </div>
  </div>
</template>

<script>
import Header from "../components/Header/index.vue";
import Table from "../components/Table/index.vue";
import Footer from "../components/Footer/index.vue";

export default {
  name: "shoppingCart",

  components: {
    Header,
    Table,
    Footer,
  },

  data() {
    return {
      cartProducts: [],
    };
  },

  mounted() {
    this.cartProducts = JSON.parse(localStorage.getItem("cart"));
  },
};
</script>

<style lang="scss" scoped>

.containerTable {
  margin-top: 5rem;
  margin-bottom: 2rem;
  display: flex;
  justify-content: center;
  position: relative;
}

.footerShoppingCartPage {
  position: absolute;
  width: 100%;
}
</style>
