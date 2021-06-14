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
    },
    data: function () {
        return {
            films: ''
        }
    },
    created: function () {
    }
}
</script>

<style lang="scss"  scoped>
    .card {
        display: flex;
        flex-direction: column;
        width: calc(100% / 6);
        height: calc((100vh / 4) - 50px);
        overflow-y: auto;
        text-align: center;
        padding: 5px;
        margin: 10px;
    }
    
</style>