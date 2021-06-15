<template>

        <div class="card">
            <h2>{{ item.title }}</h2>
            <h3>{{ item.original_title }} ({{ item.original_language }})</h3>
            <h5>VOTO: {{ item.vote_average }}/10 </h5>
        </div>

</template>

<script>

export default {
    name: 'Cards',
    props: {
        item: Object
    }    
}
</script>

<style lang="scss" scoped>
    .card {
        display: flex;
        flex-direction: column;
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
        h3 {
            color: lightgrey;
            margin: 10px 0;
        }
        h5 {
            color: white;
        }
    
</style>