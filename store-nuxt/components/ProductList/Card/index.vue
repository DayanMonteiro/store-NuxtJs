<template>

  <div class="productContainer">
    <div class="contentImage">
      <img :src="product.imageUrl" alt="">
    </div>
    <div class="productInfo" >
      <span>{{product.category}}</span>

      <h3>{{product.name}}</h3>

      <p>{{product.description}}</p>

      <h1>R$ {{product.price}}</h1>
    </div>
    <button>Adicionar ao Carrinho</button>
  </div>
</template>

<script>
  export default {
    name: "Card",
    props: [
      "product"
    ]
  }
</script >

<style lang="scss"scoped  >
  .productContainer{
    background-color: #909090;
    height: 37.5rem;
    width: 20rem;

    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  }

  .contentImage{
    background-color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .productInfo{
    background-color: #fff;
    height: 15rem;
    padding: 1rem;


    span{
      color: #8A2BE2;
      font-weight: bold;
      /* margin-top: 1rem; */
    }

    h3{
      color: #434343;
      margin-top: 1rem;
    }

    p{
      color: #909090;
      margin-top: 1rem;
    }

    h1{
      color: #434343;
      margin-top: 1rem;
    }
  }

  button{
    background-color: #fff;
    color: #8A2BE2;
    width: 100%;
    height: 4rem;
    text-transform: uppercase;
    margin-top: 0.1rem;
  }

  button:hover {
    background-color: #8A2BE2;
    color: #fff;
  }
</style>