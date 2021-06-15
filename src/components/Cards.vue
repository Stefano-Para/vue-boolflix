<template>
        <div class="container_film_telefilms">
            <!-- films  -->
            <div class="film_card">
                <h2>{{ film.title }}</h2>
                <h3>{{ film.original_title }}</h3>
                <h4> <!--  lingua + bandiera -->
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
                    <!-- to-do=spostare il v-if in methods  -->
                </h4>
                <h5>VOTO: {{ film.vote_average }}/10</h5>
            </div>

            <!-- telefilms  -->
            <div class="telefilms_card">
                <h2>{{ telefilm.name }}</h2>
                <h3>{{ telefilm.original_name }}</h3>
                <h4> 
                    Lingua: {{ telefilm.original_language }}
                    <img v-if="telefilm.original_language == 'it'"
                        src="../assets/it.png"
                        alt="">
                    <img v-else-if="telefilm.original_language == 'en'"
                    src="../assets/en.png"
                    alt="">
                    <img v-else
                        src="../assets/miss.png"
                        alt=""> 
                    
                </h4>
                <h5>{{ telefilm.vote_average }}/10</h5>
            </div>
        </div>
</template>

<script>

export default {
    name: 'Cards',
    data: function() {
        return {
            
        }
    },
    props: {
        telefilm: Object,
        film: Object,
    },
    methods: {
    },
}
</script>

<style lang="scss" scoped>
    .film_card,
    .telefilm_card {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        background-color: #8c2525;
        border-radius: 5px;
        width: calc(100% / 6);
        height: calc(100vh / 4.8);
        overflow-y: auto;
        // text-align: center;
        padding: 5px;
        margin: 5px 10px;
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