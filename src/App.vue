<template>
  <div id="app">
    <div id="big-wrap">

      <Header 
      @performSearch="searchedTitle"/>
    
      <Main :searchedItems="films" />
  
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
      // titlesInApp: '',
      films: []
    }
  },
  methods: {
    searchedTitle: function (title) {
      this.titlesInApp = title;
      console.log(this.titlesInApp)
      axios
        .get('https://api.themoviedb.org/3/search/movie', {
          params: {
              api_key: '9e009795b16be726404835f1279d61f7',
              query: this.titlesInApp,
              language: "",
              flag: ""
          }
        })
        .then(
            (res) => {
              // console.log("array intero di tutti i film: ")
              // console.log(res);
              this.films = res.data.results;
              console.log(this.films)
              // if (this.original_language == "it") {
              //   return this.language = this.language
              // }
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
    background-image: linear-gradient(to top, rgb(0 0 0), rgb(255 0 0 / 85%));
  }
//   background-color: #800e0e;
  //   min-height: 100vh;
  // }
</style>
