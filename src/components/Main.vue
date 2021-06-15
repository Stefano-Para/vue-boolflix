<template>
  <main>
    <div id="container_cards" v-if="searchedFilms.length > 0">
      <!-- mettere un v-if CAMPO DI RICERCA VUOTO => fai vedere una pagina di paraflix statica (banners o altro), v-else mostra cosa hai ricercato -->

      <Cards 
      v-for="(film, index) in searchedFilms"
      :key="index"
      :item="film"   
      />

    </div>
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
      searchedFilms: Array 
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
      #container_cards {
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