<template>
  <div class="container">

    <Card />

  </div>
</template>

<script>

import Card from './Card/index.vue';

export default {
  name: 'ProductList',

  components: {
    Card
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
</style>