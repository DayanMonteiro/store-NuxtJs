<template>
  <div>
    <Header />
    <div class="containerTable">     
      <Table />
    </div>
    <Footer />
  </div>
</template>

<script>
import Table from '../components/Table/index.vue';

  export default {
    name: "shoppingCart"
  }
</script>

<style lang="scss"scoped  > 
  .containerTable{
   // background-color: blue;
    margin-top: 5rem;
    margin-bottom: 5rem;
    display: flex;
    justify-content: center;
  }

</style>