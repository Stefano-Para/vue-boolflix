<template>
  <div id="app">

    <div id="big-wrap">

      <!-- :titles="allTitles" CANCELLARE -->
      <Header 
      @performSearch="searchedTitle"/>
    

      <Main :titlesInMain="titlesInApp" />
  
    </div>
          <!-- <h2>{{ titlesInApp }}</h2> -->
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';


export default {
  name: 'App',
  data: function () {
    return {
      // allTitles: [],
      // searchedFieldText: ''
      titlesInApp: ''
    }
  },
  // sto sbagliando dove recuperare i dati? allTitles è VUOTO per ora
  // devo spostarle i dati e rifare il computed + methods nel main? 
  computed: {
    // filteredTitle: function() {
    //   const arrayFilteredTitles = this.allTitles.filter(
    //     (element) => {
    //       return element.title.toLowerCase().includes(this.searchedFieldText.toLowerCase());
    //     }
    //   );
    //   return arrayFilteredTitles;
    // }
  },

  methods: {
    searchedTitle: function (title) {
      console.log("click su ricerca titolo");
      // console.log(title)
      // passaggio e SALVATAGGIO in APP 
      this.titlesInApp = title;
      console.log(this.titlesInApp)
      // this.searchedFieldText = title;
      // console.log(this.searchedFieldText)
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
