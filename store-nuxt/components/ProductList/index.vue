<template>
  <div class="container">


    <ul 
    >
        <li >
          <Card   />    
        </li>
      </ul>


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

  async asyncData({ $axios }) {
  const products = await $axios.$get('https://raw.githubusercontent.com/owInteractive/desafio-frontend-2020/master/produtos.json')
  return { products }

},


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
</style>