<template>
  <div>
    <Header />
    <Carousel />
    <div class="contentPage">
      <SearchProduct />
      <ProductList />
    </div>
    <Footer />

  </div>

</template>

<script>
  import Header from '../components/Header/index.vue';
  import Carousel from '../components/Carousel/index.vue';
  import SearchProduct from '../components/SearchProduct/index.vue';
  import ProductList from '../components/ProductList/index.vue';
  import Footer from '../components/Footer/index.vue';


export default {
  name: 'IndexPage',

  components: {
    Header,
    Carousel,
    SearchProduct,
    ProductList,
    Footer
  }
}
</script>


<style lang="scss"scoped >

  .contentPage{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 0;
    padding: 0;
  }
</style>