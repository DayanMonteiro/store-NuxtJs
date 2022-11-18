<template>
  <div class="cardsContainer" >
  <div class="productContainer">
    <div class="contentImage">
      <img src="https://www.lenovo.com/medias/ideapad-gaming-3-linux-gen5.png?context=bWFzdGVyfHJvb3R8OTA1MDZ8aW1hZ2UvcG5nfGg3OC9oNDEvMTQ0ODc5OTAyNzIwMzAucG5nfGUxNTM3NzViMzExM2YxYTE1NWRiOGMyYTIyMDM3YzEzMjlhMGE1NWFjZDUwOTU2MWYxZWI5NGMwNTY3YzM0OTE" alt="">
    </div>
    <div class="productInfo" >
      <span>Categoria</span>

      <h3>Nome do produto</h3>

      <p>Descrição - Lorem ipsum dolor sit, amet consectetur adipisicing elit. Doloribus repellat sequi alias cupiditate iste laudantium blanditiis assumenda nam?</p>

      <h1>R$ 1.500,00</h1>
    </div>
    <button>Adicionar ao Carrinho</button>
  </div>

  <div class="productContainer">
    <div class="contentImage">
      <img src="https://www.lenovo.com/medias/ideapad-gaming-3-linux-gen5.png?context=bWFzdGVyfHJvb3R8OTA1MDZ8aW1hZ2UvcG5nfGg3OC9oNDEvMTQ0ODc5OTAyNzIwMzAucG5nfGUxNTM3NzViMzExM2YxYTE1NWRiOGMyYTIyMDM3YzEzMjlhMGE1NWFjZDUwOTU2MWYxZWI5NGMwNTY3YzM0OTE" alt="">
    </div>
    <div class="productInfo" >
      <span>Categoria</span>

      <h3>Nome do produto</h3>

      <p>Descrição - Lorem ipsum dolor sit, amet consectetur adipisicing elit. Doloribus repellat sequi alias cupiditate iste laudantium blanditiis assumenda nam?</p>

      <h1>R$ 1.500,00</h1>
    </div>
    <button>Adicionar ao Carrinho</button>
  </div>


  <div class="productContainer">
    <div class="contentImage">
      <img src="https://www.lenovo.com/medias/ideapad-gaming-3-linux-gen5.png?context=bWFzdGVyfHJvb3R8OTA1MDZ8aW1hZ2UvcG5nfGg3OC9oNDEvMTQ0ODc5OTAyNzIwMzAucG5nfGUxNTM3NzViMzExM2YxYTE1NWRiOGMyYTIyMDM3YzEzMjlhMGE1NWFjZDUwOTU2MWYxZWI5NGMwNTY3YzM0OTE" alt="">
    </div>
    <div class="productInfo" >
      <span>Categoria</span>

      <h3>Nome do produto</h3>

      <p>Descrição - Lorem ipsum dolor sit, amet consectetur adipisicing elit. Doloribus repellat sequi alias cupiditate iste laudantium blanditiis assumenda nam?</p>

      <h1>R$ 1.500,00</h1>
    </div>
    <button>Adicionar ao Carrinho</button>
  </div>
</div>
</template>

<script>
  export default {
    name: "Card"
  }
</script >

<style lang="scss"scoped  >

  .cardsContainer{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }

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