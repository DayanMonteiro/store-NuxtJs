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
export default {
  name: 'IndexPage',

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