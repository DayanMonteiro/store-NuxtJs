<template>
  <div class="productContainer">
    <div class="contentImage">
      <img :src="product.imageUrl" alt="" />
    </div>
    <div class="productInfo">
      <span>{{ product.category }}</span>

      <h3>{{ product.name }}</h3>

      <p class="description" >{{ product.description }}</p>

      <h1> 
        {{ formatMoney(product.price) }}
      </h1>
        
   
    </div>
    <button>Adicionar ao Carrinho</button>
  </div>
</template>

<script>

import {mask} from 'vue-the-mask'

export default {
  name: "Card",
  props: ["product"],
  directives: {mask},

  methods: {
    formatMoney(value) {

    return value.toLocaleString('pt-br',{style: 'currency', currency: 'BRL'});
     
    }
  }
};


</script>

<style lang="scss" scoped>
.productContainer {
  background-color: #909090;
 
  height: 29rem;
  width: 20rem;

  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  margin: 1rem;


}

.contentImage {
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;

}

img{
  width: 10rem;
  height: 10rem;
}

.productInfo {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-color: #fff;
  height: 15rem;
  padding: 1rem;

  span {
    color: #8a2be2;
    font-weight: bold;
    /* margin-top: 1rem; */
  }

  h3 {
    color: #434343;
    margin-top: 1rem;
  }

  p {
    color: #909090;
    margin-top: 1rem;
  }

  h1 {
    color: #434343;
    margin-top: 1rem;
  }

  /* .price {
    color: #434343;
    margin-top: 1rem;
  } */
}

button {
  background-color: #fff;
  color: #8a2be2;
  width: 100%;
  height: 4rem;
  text-transform: uppercase;
  margin-top: 0.1rem;
}

button:hover {
  background-color: #8a2be2;
  color: #fff;
}



/* xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx */

.description {
  max-height: 10rem;
  overflow: auto;
}

</style>
