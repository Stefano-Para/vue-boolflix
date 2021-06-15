<template>

        <div class="card">
            <h2>Titolo: {{ item.title }}</h2>
            <h3>Titolo originale: {{ item.original_title }}</h3>
            <h4>Lingua: {{ item.original_language }} <img :src="flag" alt=""> </h4>
            <h5>VOTO: {{ item.vote_average }}/10 </h5>
        </div>

</template>

<script>

export default {
    name: 'Cards',
    data: function() {
        return {
            flag: ''
        }
    },
    props: {
        item: Object
    },
    methods: {
    },
    created: function() {
        if (this.item.original_language == "it" ) {
            this.flag = require("../assets/it.png");
        } else if (this.item.original_language == "en" ) {
            this.flag = require("../assets/en.png");
        }
    }
}
</script>

<style lang="scss" scoped>
    .card {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        background-color: #286687;
        border-radius: 5px;
        width: calc(100% / 6);
        height: calc(100vh / 4.8);
        overflow-y: auto;
        text-align: center;
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