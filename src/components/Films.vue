<template>
    <div class="container-card background">
        <div class="card-img ">
            <img
            v-if="film.poster_path != film.imgNull"
            :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`" alt="">
            <div id="img-not-found" v-else>
                <h2>Poster-Image not found</h2>
            </div>
        </div>
        <div class="card-info">
            <!-- title + language + flag -->
            <h2 class="uppercase">
                {{ film.title }}
                <h6>({{ film.original_language }}<img v-if="film.original_language == 'it'"
                    src="../assets/it.png"
                    alt="">
                <img v-else-if="film.original_language == 'en'"
                src="../assets/en.png"
                alt="">
                <img v-else
                    src="../assets/miss.png"
                    alt="">)</h6>
                
                
            </h2>
            <!-- original title  -->
            <h3 class="uppercase">{{ film.original_title }}</h3>    
            <!-- overview -->
            <section>
                <h6 class="uppercase">Overview:</h6>
                <p>{{ film.overview}} </p>
            </section>
            <!-- rating vote + stars -->
            <h5>
                <span class="uppercase">voto: </span>{{ film.vote_average }}/10
                <span>
                     <!-- <i
                        v-for="i in starCount()"
                        :key="i" 
                        class="fas fa-star"></i>
                    <i
                        v-for="i in 5-starCount()"
                        :key="i + film.title" 
                        class="far fa-star"
                    ></i> -->
                    <i
                        v-for="i in 5"
                        :key="i"
                        :class="i <= starCount() ? 'fas fa-star' : 'far fa-star'"
                    ></i>
                </span>
            </h5>
        </div>            
    </div>
</template>

<script>

export default {
    name: 'Films',
    data: function() {
        return {
            imgNull: "null",
        }
    },
    props: {
        film: Object,
    },
    methods: {
        starCount: function() {
            return Math.round(this.film.vote_average / 2);
        }
    }
}
</script>

<style lang="scss" scoped>
 @import "../assets/cards.scss";
</style>