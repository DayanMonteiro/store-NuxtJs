<template>
  <div class="container">
    <h2>Encontre seu produto</h2>

    <div id="search">
     <input type="text" id="txtSearch" placeholder="Pesquisar..."/>
     <button>
       <img src="../../resources/icons/magnifying-glass.svg" id="btnBusca" alt="Buscar"/>

     </button>
    </div>



  </div>
</template>

<script>
export default {
  name: 'SearchProduct'
}

</script>

<style lang="scss"scoped >

  .container{
    display: flex;
    align-items: center;
    margin-top: 5rem;
//justify-content: center;
    /* background-color: red ; */
    width: 57%;
    height: 5.5rem;

    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;


  }

  h2{
      color: #909090;
      margin-left: 3rem;
    }

  #search{
      display: flex;
      align-items: center;
      margin-left: 1rem;
  }



  #txtSearch{
    float:left;
    padding-left: 1rem;
    font-style:italic;
    font-size:18px;
    border:none;
    height: 3rem;
    width: 43rem; 
    border: 1px solid gray;
    border-bottom-left-radius: 5px;
    border-top-left-radius: 5px;
  }

  button{
    background-color: #8e36b7;
    width: 3rem;
    height: 3rem;
    border: none;
    border-bottom-right-radius: 5px;
    border-top-right-radius: 5px;
    margin-left: -2rem;
  }

  img{
    width: 1.3rem;
   
  }
</style>


