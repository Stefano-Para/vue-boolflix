<template>
  <div id="app">



  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  components: {
    
  },
  props: {

  },
  // AXIOS DOVE DEVE ESSERE RICHIAMATO? NEL MIO CREATED O AL RESEARCH? 
  created: function () {
    axios
    .get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: '9e009795b16be726404835f1279d61f7',
        query: "ritorno",
        language: "it-IT"
      }
    })
    .then(
      (res) => {
        console.log(res);
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
</style>
