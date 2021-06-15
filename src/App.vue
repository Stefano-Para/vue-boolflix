<template>
  <div id="app">
    <div id="big-wrap">

      <Header 
      @performSearch="searchedTitle"/>
    
      <Main
      :searchedFilms="films"
       />
  
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';

export default {
  name: 'App',
  data: function () {
    return {
      // searchedText: '',
      films: []
    }
  },
  methods: {
    searchedTitle: function (title) {
      this.searchedText = title;
      console.log(this.searchedText)

      axios.all ([

        // telefilm
        axios
          .get('https://api.themoviedb.org/3/search/tv', {
            params: {
                api_key: '9e009795b16be726404835f1279d61f7',
                query: this.searchedText,
                language: "",
            }
          }),

        // film 
        axios
          .get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: '9e009795b16be726404835f1279d61f7',
                query: this.searchedText,
                language: "",
            }
          })
        ])
        .then(
            (res) => {
              this.films = res.data.results;
              // I film trovati con la ricerca 
              console.log(this.films)
            },
        )
    }
  },
  components: {
    Header,
    Main
  },
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css';
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  #big-wrap {
    min-height: 100vh;
    background-image:
      linear-gradient(
        to top,
        rgb(0 0 0) 70%,
        rgb(255 0 0 / 85%)
      );
  }
//   background-color: #800e0e;
  //   min-height: 100vh;
  // }
</style>
