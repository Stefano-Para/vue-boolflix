<template>
  <main>

    <h2>Si vede anche in main che hai cercato: "{{ titlesInMain }}"</h2>

    <div id="container_cards">
      <!-- mettere un v-if CAMPO DI RICERCA VUOTO => fai vedere una pagina di paraflix statica (banners o altro), v-else mostra cosa hai ricercato -->

      <!-- dato arrivato in MAIN, come posso fare ad inserirlo in query?  -->
      

      <Cards 
      v-for="(film, index) in films"
      :key="index"
      :item="film"   
      />
    </div>
    

  </main>
</template>

<script>
import axios from 'axios';
import Cards from './Cards.vue';

export default {
    name: "Main",
    components: {
        Cards,
    },
    data: function () {
        return {
            films: [],
            titles: [],
        }
    },
    props: {
      titlesInMain: String
    },
    methods: {
      
    },
    // bisogna spostarlo da created in methods? 
    created: function () {
    axios
        .get('https://api.themoviedb.org/3/search/movie', {
        params: {
            api_key: '9e009795b16be726404835f1279d61f7',
            // in questa query devo fare in modo di inserire il mio dato proveniente da HEADER tramite INPUT e fare il filter con quella parola inseria (tolti gli spazi)
            // qui è da inserire il titlesInMain
            query: "prova",
            language: "it-IT"
        }
        })
        .then(
            (importAxios) => {
                // console.log(importAxios);
                this.films = importAxios.data.results;
                console.log(this.films)

                this.films.forEach(
                  (element) => {
                    this.titles.push(element.title)
                  }
                );             
            }
        )
  }
}
</script>

<style  lang="scss" scoped>
  main {
    margin: 0 auto;
    display: inline-block;
    // overflow: scroll;
  }
  #container_cards {
    width: 90%;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
  }
  // cancellare 
  h2 {
    width: 500px;
    color: white;
    size: 2em;
    margin: 0 auto;
  }
</style>