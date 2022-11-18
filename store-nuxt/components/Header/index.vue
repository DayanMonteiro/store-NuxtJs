<template>
  <div class="container" >
    <div class="logo">
      <h1 class="logoFirstname" >Mkt</h1>
      <h1 class="logoSecondName">Plance</h1>
    </div>
    <div class="products" >
      <p class="paragraph" >Produtos</p>
      <img class="cart" src="../../resources/icons/shopping-cart.svg" />
      <div class="amount">
          <p class="amountProducts">2</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
name: 'Header'
}
</script>


<style lang="scss"scoped >
  .container{
    /* background-color: gray; */
    display: flex;
    align-items: center;
    justify-content: space-around;
    height: 6rem;
    box-shadow: rgba(0, 0, 0, 0.15) 0px 3px 0px 0px;
  }

  .logo {
    display: flex;
    flex-direction: row;
    
    .logoFirstname{
      color: #A9A9A9;
    }

  .logoSecondName{
      color:blueviolet
    }

  }


  .products{
    display: flex;
    flex-direction: row;

    .paragraph{
      color: #A9A9A9;
      margin-right: 1.5rem;
    }

    .cart {
      color: #8A2BE2;
    }

    .amount{
      background-color: #FF0000;
      border-radius: 50%;
      margin-top: 1.5rem;
      height: 0.8rem;
      width: 0.8rem;
    }

    .amountProducts{
      color: #FFFFF0;
      margin-top: 0rem;
      margin-left: 0.2rem;
      font-size: 0.8rem;
      font-weight: bold;
      }
  }

</style>