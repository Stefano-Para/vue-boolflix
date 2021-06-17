<template>
  <main>
    
    <!-- se trovo in films  -->
    <div class="container_films" v-if="searchedFilms.length > 0">
      <h1>
        I TUOI FILM:
      </h1>
      <Films
        v-for="(film, index) in searchedFilms"
        :key="index"
        :film="film"   
      />
    </div>
    
    <!-- se trovo in telefilms  -->
    <div class="container_telefilms" v-if="searchedTelefilms.length > 0">
      <h1>
        I TUOI TELEFILM:
      </h1>
      <Telefilms
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
import Films from './Films.vue';
import Telefilms from './Telefilms.vue';

export default {
    name: "Main",
    components: {
        Films,
        Telefilms
    },
    props: {
      searchedFilms: Array,
      searchedTelefilms: Array
    }
}
</script>

<style  lang="scss" scoped>
  main {
    width: 100%;
    margin: 100px auto 0;
    display: inline-block;
    position: relative;
      .container_films,
      .container_telefilms {
      width: 90%;
      margin: 50px auto 80px;
      display: flex;
      flex-wrap: wrap;
      position: relative;
        h1 {
          color: white;
          position: absolute;
          top: -40px;
          left: 10px;
        }
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