<template>
  <div>
    <Header />
    <div class="contentForm">
      <CheckoutForm />
    </div>
    <Footer />
  </div>
</template>

<script>
  export default {
    name: "checkout"
  }
</script>

<style lang="scss"scoped >

  .contentForm{
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>