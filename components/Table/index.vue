<template>
  <div class="container" v-if="cartProducts.length > 0">
    <div>
      <table class="contentTable">
        <thead class="contentSection">
          <tr class="bottomLine">
            <th class="smallColumn"></th>
            <th class="bigColumn">Produtos</th>
            <th class="bigColumn">Quantidade</th>
            <th class="bigColumn">Valor Unitário</th>
            <th class="mediumColumn">Total</th>
          </tr>
        </thead>
        <tbody class="contentSection">
          <tr
            class="bottomLine"
            v-for="product in cartProducts"
            :key="product.id"
          >
            <td class="smallColumn" @click="removeFromCart(product)">
              <img class="iconSmall" src="../../resources/icons/garbage.svg" />
            </td>
            <td class="bigColumn">
              <span>{{ product.category }}</span>
              <p>{{ product.name }}</p>
            </td>
            <td class="bigColumn">
              <div class="quantityCounter">
                <button class="subtraction">-</button>
                <p class="quantity">{{ product.quantity }}</p>
                <button class="multiplication">+</button>
              </div>
            </td>
            <td class="bigColumn">
              <b> {{ formatMoney(product.price) }}</b> à vista <br />
              ou 10x {{ formatMoney(product.price / 10) }}
            </td>
            <td class="mediumColumn">
              <b> {{ formatMoney(product.price * product.quantity) }}</b> à
              vista <br />
              ou 10x
              {{ formatMoney((product.price * product.quantity) / 10) }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="finalPrice bottomLine">
      <div class="cashPayment">
        <p>Total à Vista</p>
        <span>
          {{
            formatMoney(
              cartProducts?.reduce((total, current) => total + current.price, 0)
            )
          }}
        </span>
        <br />
      </div>
      <div class="paymentInstallments">
        <p>Total Parcelado</p>
        <span
          >em até
          <b
            >10 x
            {{
              formatMoney(
                cartProducts?.reduce(
                  (total, current) => total + current.price,
                  0
                ) / 10
              )
            }}</b
          >
          <br />(Total
          {{
            formatMoney(
              cartProducts?.reduce((total, current) => total + current.price, 0)
            )
          }})</span
        >
      </div>
    </div>
    <div class="checkout">
      <button class="cleanCart">
        <img src="../../resources/icons/garbage.svg" />
        <p>Limpar carrinho</p>
      </button>
      <div class="containerButton">
        <button class="continueShopping">Continuar Comprando</button>
        <a href="/checkout">
          <button class="purchase">Concluir Compra</button>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Table",
  props: {
    cartProducts: [],
  },
  methods: {
    formatMoney(value) {
      return value.toLocaleString("pt-br", {
        style: "currency",
        currency: "BRL",
      });
    },

    removeFromCart(product) {
      const newCart = this.cartProducts.filter((p) => p.id !== product.id);

      console.log("newCart", newCart);

      localStorage.setItem("cart", JSON.stringify(newCart));

      this.cartProducts = newCart;
    },
  },
};
</script>

<style lang="scss" scoped>
.contentSection {
  height: 3rem;
}
.container {
  padding: 0;
  margin: 0;
  width: 58%;
}

th {
  text-transform: uppercase;
  color: #474747;
  text-align: left;
  padding-left: 1rem;
}

td {
  color: #434343;
  padding-left: 1rem;
  height: 6rem;

  span {
    color: #8d36b8;
  }

  p {
    width: 10rem;
    text-transform: uppercase;
    font-weight: bold;
  }
}

.quantityCounter {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  width: 5.5rem;
}

.subtraction {
  border: 1px solid #868686;
  width: 4rem;
  height: 1.7rem;
}

.multiplication {
  border: 1px solid #868686;
  width: 4rem;
  height: 1.7rem;
}

.quantity {
  display: flex;
  align-items: center;
  justify-content: center;
  border-top: 1px solid #868686;
  border-bottom: 1px solid #868686;
  height: 1.7rem;
}

.iconSmall {
  width: 0.8rem;
}

.smallColumn {
  width: 2rem;
}

.mediumColumn {
  width: 20rem;
  padding-left: 0;
}

.bigColumn {
  width: 35rem;
}
.bottomLine {
  box-shadow: rgba(0, 0, 0, 0.15) 0px 1px 0px 0px;
}

.finalPrice {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: center;
  height: 10rem;
}

.cashPayment {
  width: 20rem;
  display: flex;
  flex-direction: row;
  align-items: baseline;

  p {
    text-transform: uppercase;
    font-weight: bold;
    color: #474747;
  }

  span {
    color: #8d36b8;
    font-weight: bold;
    font-size: 1.5rem;
    margin-left: 3rem;
  }
}

.paymentInstallments {
  width: 20rem;
  display: flex;
  flex-direction: row;
  align-items: baseline;
  justify-content: space-between;
  margin-top: 2rem;

  p {
    text-transform: uppercase;
    font-weight: bold;
    color: #474747;
  }

  span {
    color: #474747;
  }
}

.purchase {
  background-color: #8d36b8;
  color: #fff;
  width: 15rem;
  height: 3rem;
  font-weight: bold;
  border-radius: 0.2rem;
}

.purchase:hover {
  background-color: #fff;
  color: #8a2be2;
}

.continueShopping {
  background-color: #cfcfcf;
  color: #434343;
  width: 15rem;
  height: 3rem;
  font-weight: bold;
  border-radius: 0.2rem;
}
.continueShopping:hover {
  background-color: #8d36b8;
  color: #fff;
}

.cleanCart {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-start;

  p {
    color: #626262;
  }
}

img {
  width: 1rem;
  margin-right: 0.5rem;
  cursor: pointer;
}
.checkout {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin-top: 3rem;
}

.containerButton {
  display: flex;
  justify-content: space-between;
  width: 31rem;
  margin-bottom: 2rem;
}
</style>
