<template>
  <div class="container">
  <div class="containerTable" >
    <table class="contentTable">
      <thead>
        <tr class="bottomLine">
          <th>Produtos</th>
          <th>Quantidade</th>
          <th>Valor Unitário</th>
          <th>Total</th>
        </tr>
      </thead>
      <tbody>
        <tr class="bottomLine">
          <td>Notebook Acer</td>
          <td>01</td>
          <td>R$ 1.500,00</td>
          <td>R$ 1.500,00</td>
        </tr>
      </tbody>
    </table>
  </div>
  <div class="finalPrice">
          <p>Total à Vista</p> <span>R$ 1.500,00</span><br />
          <p>Total Parcelado</p> <span>em até <b>10 x R$ 150,00</b> (Total R$ 1.500,00)</span>
    </div>
      <section class="checkout" >
        <div class="cleanCart">
        <img src="../../resources/icons/garbage.svg" />
        <p>Limpar carrinho</p>
      </div>
      <div>
          <button class="continueShopping">Continuar Comprando</button>
          <button class="purchase">Concluir Compra</button>
      </div>
    </section>
  </div>
   
</template>

<script>
  export default {
    name: "Table"
  }

</script>

<style lang="scss"scoped  > 

  .container{
    background-color: aquamarine;
    width: 52%;
  }
  .containerTable{
    background-color: antiquewhite;
    /* display: flex;
    align-items: center;
    justify-content: space-between; */
   
  }

    .contentTable{
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: space-between; 
    }

  th{
    text-transform: uppercase;
    color: #434343;
    /* width: 23rem; */
    border: 2px solid blue;
  }

  td{
    text-transform: uppercase;
    color: #434343;
    border: 2px solid blue;
    /* width: 23rem; */
  }
  .bottomLine{
    box-shadow: rgba(0, 0, 0, 0.15) 0px 3px 0px 0px;
  }

  .finalPrice{
    background-color: rebeccapurple;
    display: flex;
    align-items: flex-end;
    justify-content: flex-end;

    margin-top: 1rem;
    height: 6rem;
  }

  .purchase{
    background-color: #8A2BE2;
    color: #fff;
    width: 15rem;
    height: 3rem;
    font-weight: bold;
    /* margin-top: 0.1rem; */
    border-radius: 0.2rem;
  }

    .cleanCart{
      display: flex;
      flex-direction: row;
      justify-content: flex-start;
    }

    img{
      width: 1rem;
      margin-right: 0.5rem;
    }
  .purchase:hover {
    background-color: #fff;
    color: #8A2BE2;
  }

  .continueShopping{
    background-color: #CFCFCF;
    color: #434343;
    width: 15rem;
    height: 3rem;
    font-weight: bold;
    border-radius: 0.2rem;
  }

  .checkout{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
</style>