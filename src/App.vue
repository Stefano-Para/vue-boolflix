<template>
  <div id="app">

    <div id="big-wrap">
     <Header />

    <Main /> 
    </div>

  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';


export default {
  name: 'App',
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
