<template>
  <div id="app">

    <div id="big-wrap">
     <Header 
     :titles="allTitles"/>

    <Main
    @titlesFromMain="searchTitle" /> 
    </div>

  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';


export default {
  name: 'App',
  data: function () {
    return {
      allTitles: []
    }
  },
  methods: {
    searchTitle: function (array) {
      this.allTitles = array;
    }
  },
  components: {
    Header,
    Main
  },
  props: {

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
    background-color: #800e0e;
    min-height: 100vh;
  }

</style>
