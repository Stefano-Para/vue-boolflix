<template>
  <main>
    <div id="container_cards">
      <!-- mettere un v-if CAMPO DI RICERCA VUOTO => fai vedere una pagina di paraflix statica (banners o altro), v-else mostra cosa hai ricercato -->
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
    created: function () {
    axios
        .get('https://api.themoviedb.org/3/search/movie', {
        params: {
            api_key: '9e009795b16be726404835f1279d61f7',
            query: "r",
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

                this.$emit('titlesFromMain', this.title)

                // ciclo forEach per visualizzazione in pagina:
                
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
</style>