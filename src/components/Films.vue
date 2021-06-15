<template>
    <div class="card">
        <h2>{{ film.title }}</h2>
        <h3>{{ film.original_title }}</h3>
        <h4> 
            Lingua: {{ film.original_language }}
            <img v-if="film.original_language == 'it'"
                src="../assets/it.png"
                alt="">
            <img v-else-if="film.original_language == 'en'"
            src="../assets/en.png"
            alt="">
            <img v-else
                src="../assets/miss.png"
                alt=""> 
        </h4>
        <h5>VOTO: {{ film.vote_average }}/10</h5>
    </div>            
</template>

<script>

export default {
    name: 'Films',
    props: {
        film: Object,
    },
}
</script>

<style lang="scss" scoped>
    .card {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        background-color: #8c2525;
        border-radius: 5px;
        width: calc(100% / 6);
        height: calc(100vh / 4.8);
        overflow-y: auto;
        padding: 5px;
        margin: 10px;
    }
        .card::-webkit-scrollbar {
            width: 0;  /* Remove scrollbar space */
        }
        h2 {
            font-size: 1.4em;
        }
        h3 {
            color: lightgrey;
            margin: 5px 0;
            font-size: 0.9em;
        }
        h4 {
            color: lightgrey;
            img {
                height: 12px;
            }
        }
        h5 {
            color: white;
            margin-top: 5px;
        }
    
</style>