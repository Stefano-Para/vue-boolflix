<template>
    <div class="container-card">
        <div class="card-img">
            <img
            v-if="telefilm.poster_path != telefilm.imgNull"
            :src="`https://image.tmdb.org/t/p/w342${telefilm.poster_path}`" alt="">
            <div id="img-not-found" v-else>
                <h2>Poster-Image not found</h2>
            </div>
        </div>
        <div class="card-info">
            <!-- title + language + flag -->
            <h2 class="uppercase">
                {{ telefilm.name }}
                <h6>
                    ({{ telefilm.original_language }}
                <img v-if="telefilm.original_language == 'it'"
                    src="../assets/it.png"
                    alt="">
                <img v-else-if="telefilm.original_language == 'en'"
                src="../assets/en.png"
                alt="">
                <img v-else
                    src="../assets/miss.png"
                    alt="">)
                </h6>
            </h2>
            <!-- original title  -->
            <h3 class="uppercase">{{ telefilm.original_name }}</h3>    
            <!-- overview -->
            <section>
                <h6 class="uppercase">Overview:</h6>
                <p>{{ telefilm.overview}} </p>
            </section>
            <!-- rating vote + stars -->
            <h5>
                <span class="uppercase">voto: </span>{{ telefilm.vote_average }}/10
                <span>
                     <!-- <i
                        v-for="i in starCount()"
                        :key="i" 
                        class="fas fa-star"></i>
                    <i
                        v-for="i in 5-starCount()"
                        :key="i + telefilm.title" 
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
    name: 'Telefilms',
    data: function() {
        return {
            imgNull: "null",
        }
    },
    props: {
        telefilm: Object,
    },
    methods: {
        starCount: function() {
            return Math.round(this.telefilm.vote_average / 2);
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/cards.scss";
</style>