<template>
    <div class="container-card">
        <div class="card-img">
            <img
            v-if="film.poster_path != film.imgNull"
            :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`" alt="">
            <div id="img-not-found" v-else>
                <h2>Poster-Image not found</h2>
            </div>
        </div>
        <div class="card-info">        
            <h2>Titolo: {{ film.title }}</h2>
            <h3>Titolo originale: {{ film.original_title }}</h3>
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
        // overflow-y: auto;
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
            padding: 15px;
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