<template>
  <main>
    
    <!-- se trovo in films  -->
    <div class="container_cards" v-if="searchedFilms.length > 0">

      <h2>I tuoi FILM</h2>
      
      <Cards 
      v-for="(film, index) in searchedFilms"
      :key="index"
      :film="film"   
      />
    </div>
    
    <!-- se trovo in telefilms  -->
    <div class="container_cards" v-else-if="searchedTelefilms.length > 0">

      <h2>I tuoi TELEFILM</h2>

      <Cards
      v-for="(telefilm, index) in searchedTelefilms"
      :key="index"
      :telefilm="telefilm"
      />
    </div> 

    <!-- se non trovo nulla  -->
    <div id="container_else" v-else>
        <h2>La tua ricerca non ha prodotto nessun risultato.</h2>
        <h3>Cerca il tuo film preferito nella barra di ricerca.</h3>
    </div>
  </main>
</template>

<script>
// import axios from 'axios';
import Cards from './Cards.vue';

export default {
    name: "Main",
    components: {
        Cards,
    },
    data: function () {
        return {
        }
    },
    props: {
      searchedFilms: Array,
      searchedTelefilms: Array
    },
}
</script>

<style  lang="scss" scoped>
  main {
    width: 100%;
    margin: 0 auto;
    display: inline-block;
    position: relative;
    top: 80px;
      .container_cards {
      width: 90%;
      margin: 0 auto;
      display: flex;
      flex-wrap: wrap;
      }
      #container_else {
        width: 90%;
        height: calc(100vh - 250px);
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
          h2,
          h3 {
            margin: 10px 0;
            text-align: center;
            color: white;
          }
      }
}
</style>