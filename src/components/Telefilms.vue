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
            <h2>Titolo: {{ telefilm.title }}</h2>
            <h3>Titolo originale: {{ telefilm.original_title }}</h3>
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
            <h5>
                VOTO: {{ telefilm.vote_average }}/10
                <span>
                    <!-- <i
                        v-for="i in starCount()" :key="i" 
                        class="fas fa-star"></i>
                    <i
                        v-for="i in 5-starCount()" :key="i" 
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
    .container-card {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        background-color: black;
        border-radius: 5px;
        width: 19%;
        height: 350px;
        border-radius: 10px;
        margin: 2px;
        .card-img img {
            width: 100%;
            height: 350px;
            border-radius: 10px;
        }
        .card-img {
            position: absolute;
            height: 350px;
            width: 19%;
            :hover {
            opacity: 0.2;
            }
            #img-not-found {
                width: 100%;
                height: 100%;
                background-color: black;
                display: flex;
                align-items: center;
                h2 {
                    padding: 10px;
                    line-height: 40px;
                    text-align: center;
                    color: red;
                    text-transform: uppercase;
                }
            }
        }
    } // chiusura .container-card
        .card-info {
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            height: 100%;
            padding: 20px;
            line-height: 20px;
            h2 {
                color: white;
                font-size: 1.4em;
            }
            h3 {
                color: white;
                margin: 5px 0;
                font-size: 0.9em;
            }
            h4 {
                color: white;
                img {
                    height: 14px;
                    width: 20px;
                }
            }
            h5 {
                color: white;
                margin-top: 5px;
            }
        } // chiusura card info
    
</style>