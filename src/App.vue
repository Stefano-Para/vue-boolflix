<template>
  <div id="app">
    <div id="big-wrap">

      <Header 
      @performSearch="searchedTitle"/>
    
      <Main
      :searchedFilms="films"
      :searchedTelefilms="telefilms"
       />

       {{ suggestedFilms }}
  
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
      films: [],
      telefilms: [],
      suggestedFilms: '',
    }
  },
    components: {
    Header,
    Main
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
              this.films = res[1].data.results;
              this.telefilms = res[0].data.results;
              // this.telefilms = res
              // I film trovati con la ricerca 
              console.log(res)
            },
        )
    } // chiusura searchedTitle
  },
  created: function() {
      axios.all ([
        // telefilm
        axios
          .get('https://api.themoviedb.org/3/search/tv?api_key=9e009795b16be726404835f1279d61f7&query=evangelion&language=it-IT'),
        // film 
        axios
          .get('https://api.themoviedb.org/3/search/movie?api_key=9e009795b16be726404835f1279d61f7&query=evangelion&language=it-IT')
        ])
        .then (
          (res) => {
            this.films = res[1].data.results;
              this.telefilms = res[0].data.results;
              // this.telefilms = res
              // I film trovati con la ricerca 
              console.log(res)
          }
        )
  }
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
        rgb(0 0 0),
        rgb(255 0 0 / 90%)
      );
  }
//   background-color: #800e0e;
  //   min-height: 100vh;
  // }
</style>
