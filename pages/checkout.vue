<template>
  <div>
    <Header />
    <div class="contentForm">
      <CheckoutForm />
    </div>
    <div class="footerCheckoutPage">
      <Footer />
    </div>
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
    position: relative;
  }

  .footerCheckoutPage{
    position: absolute;
    width: 100%;
    bottom: 0;
  }
</style>