<template>
  <div class="containerHeader">
    <div class="logo">
      <a href="/" class="textLogo" >
        <h1 class="logoFirstname">Mkt</h1>
        <h1 class="logoSecondName">Place</h1>
      </a>
    </div>
    <a href="/shoppingCart" class="products">
      <p class="paragraph">Produtos</p>
      <img class="cart" src="../../resources/icons/shopping-cart.svg" />
      <div class="amount">
        <p class="amountProducts">{{ quantity }}</p>
      </div>
    </a>
  </div>
</template>

<script>
export default {
  name: "Header",
  
  computed: {
    quantity() {
      if (process.client) {
        return localStorage.getItem("cartItemsQty") || 0;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.containerHeader {
  height: 6rem;
  box-shadow: rgba(0, 0, 0, 0.15) 0px 3px 0px 0px;
  display: flex;
  align-items: center;
  justify-content: space-around;
  width: 100%;
  margin: 0;
  padding: 0;
}

.logo {
  display: flex;
  flex-direction: row;


  .logoFirstname {
    color: #909090;
  }

  .logoSecondName {
    color: #8e36b7;
   
  }
}

.textLogo{
  text-decoration: none;
  display: flex;
}

.products {
  display: flex;
  flex-direction: row;
  align-items: center;
  text-decoration: none;

  .paragraph {
    color: #909090;
    margin-right: 1.5rem;
  }

  .cart {
    color: #8a2be2;
  }

  .amount {
    background-color: #ed1c24;
    border-radius: 50%;
    margin-top: 1.2rem;
    height: 1rem;
    width: 1rem;

    display: flex;
    align-items: center;
    justify-content: center;
  }

  .amountProducts {
    color: #fffff0;
    font-size: 0.7rem;
    font-weight: bold;
  }
}
</style>
