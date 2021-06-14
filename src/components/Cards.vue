<template>
    <div id="contenitore_cards">
        <h2>questo è da CARDS</h2>
        <ul>
            <li>
                
                <h2>TITOLO: {{ film.title }}</h2>

                <h3>TITOLO ORIGINALE: {{ film.original_title }}</h3>

                <h4>LINGUA: {{ film.original_language }}</h4>

                <h5>VOTO: {{ film.vote_average }}/10</h5>
            </li>
        </ul>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Cards',
    data: function () {
        return {
            films: ''
        }
    },
    props: {

    },
    // AXIOS DOVE DEVE ESSERE RICHIAMATO? NEL MIO CREATED O AL RESEARCH? 
    // devo farlo all'interno dell'header che viene richiamata QUANDO si preme il pulsante di ricerca. Quando si carica la prima volta la pagina la pagina è vuota
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
            (importAxios) => {
                // console.log(importAxios);
                this.films = importAxios.data.results;
                console.log(this.films)

                // ciclo forEach per visualizzazione in pagina:
                
            }
        )
    }

}
</script>

<style scoped lang="scss">

</style>