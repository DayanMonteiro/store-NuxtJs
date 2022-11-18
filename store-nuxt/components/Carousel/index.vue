<template>
  <v-carousel :show-arrows="false" >
    <v-carousel-item
      v-for="(item,i) in items"
      :key="i"
      :class="item.class"
      reverse-transition="fade-transition"
      transition="fade-transition"
    > 
    <div  :class="item.txtClass">
      <div class="textContent">
        <h1 class="txtClassTitle" >
          {{item.src}}
        </h1 >
        <p class="txtClassText">As melhores ofertas</p>
      </div>
    </div>
     
  </v-carousel-item>
  </v-carousel>
</template>

<script>
export default {
  name: 'Carousel',

    data () {
      return {
        items: [
          {
            src: 'Notebooks',
            class: "carousel1",
            txtClass: "txtcarousel1"
          },
          {
            src: 'Geladeiras',
            class: "carousel2",
            txtClass: "txtcarousel2"

          },

        ],
      }
    },
  }
</script>

<style lang="scss"scoped >

  .container{
    h1{
      color: #444141;
    }
  }
  
    .carousel1{
      background-image: linear-gradient( to right, #8A2BE2, #d794f6);
    }

    .carousel2{
      background-image: linear-gradient( to right, #8A2BE2, #d794f6);
    }


    .textContent {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      margin-top: 12rem;
      margin-right: 26rem;
    }
    .txtClassTitle{
      color: #fff;
      font-size: 5rem;
    }

    .txtClassText{
      color: #fff;
      font-size: 2.5rem;
    }
</style>