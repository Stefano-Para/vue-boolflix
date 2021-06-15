<template>
    <div class="card">
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
</template>

<script>
export default {
    name: "Telefilms",
    props: {
        telefilm: Object,
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
        width: calc(100% / 5.5);
        height: calc(100vh / 4.8);
        overflow-y: auto;
        padding: 5px;
        margin: 10px;
    }
        .card::-webkit-scrollbar {
            width: 0;
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