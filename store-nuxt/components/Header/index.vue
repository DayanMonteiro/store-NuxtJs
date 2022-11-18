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
    height: 6rem;
    box-shadow: rgba(0, 0, 0, 0.15) 0px 3px 0px 0px;
    display: flex;
    align-items: center;
    justify-content: space-around;
  }

  .logo {
    display: flex;
    flex-direction: row;
    
    .logoFirstname{
      color: #909090;
    }

  .logoSecondName{
      color: #8e36b7;
    }

  }


  .products{
    display: flex;
    flex-direction: row;

    .paragraph{
      color: #909090;
      margin-right: 1.5rem;
    }

    .cart {
      color: #8A2BE2;
    }

    .amount{
      background-color: #ed1c24;
      border-radius: 50%;
      margin-top: 1.2rem;
      height: 1rem;
      width: 1rem;

      display: flex;
      align-items: center;
      justify-content: center;
    }

    .amountProducts{
      color: #FFFFF0;
    //  margin-top: 0.1rem;
     // margin-left: 0.2rem;
      font-size: 0.7rem;
      font-weight: bold;
      }
  }

</style>