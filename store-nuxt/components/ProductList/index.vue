<template>
  <div class="container">

    <div class="cardsContainer" v-if="productsList.length !== 0" >
          <!-- <Card  v-for="(product) in productsList" :key="product.id" :product="product" />   -->
          <!-- xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx -->
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
      <!-- xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx -->
    </div>
    
    <h1>hue</h1>
  </div>
</template>

<script>

import Card from './Card/index.vue';
import { dataApi } from '../../services/dataApi';

export default {
  name: 'ProductList',

  components: {
    Card
  },

  data(){
    return {
      productsList: []
    }
  },

  methods: {
    async asyncData() {
      try {      
        const response = await dataApi.get('https://raw.githubusercontent.com/owInteractive/desafio-frontend-2020/master/produtos.json')
        this.pruductsList = response.data
      } catch (error) {
        this.pruductsList = []
      }
  }
},

mounted() {
  this.asyncData()
}

}
</script>

<style lang="scss"scoped >

  .container{
   // background-color: antiquewhite; 
    height: 100%;
    width: 57%;
    margin-top: 5rem;
    margin-bottom: 5rem;

    h1{
      color: #444141;
    }
  }

  .cardsContainer{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }

  // xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 

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