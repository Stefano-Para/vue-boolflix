<template>
  <main>
    <Cards v-for="(film, index) in films" :key="index"/>
  </main>
</template>

<script>
import Cards from './Cards.vue';

export default {
    name: "Main",
    components: {
        Cards,
    },
    data: function () {
        return {
            films: ''
        }
    },
}
</script>

<style>

</style>