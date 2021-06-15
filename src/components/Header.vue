<template>
    <header>
        <div id="container_navbar">
            <div id="logo">
                <img src="https://fontmeme.com/permalink/210614/5dd112198b1bd4cee91a23e783cdc370.png" alt="">
            </div>

            <div id="searchbar">
                <input
                    type="text"
                    placeholder="Ricerca.."
                    v-model="searchTitle"
                    @keyup.enter="$emit('performSearch', lowerSearchTitle)">
            </div>

            <div id="show-searched">
                <h2>I titoli correlati a: <h6>"{{ lowerSearchTitle }}"</h6></h2>
            </div>
            
        </div>
    </header>
</template>

<script>

export default {
    name: 'Header',
    data: function() {
        return {
            searchTitle: ''
        }
    },
    computed: {
        lowerSearchTitle: function() {
            return this.searchTitle.toLowerCase()
        }
    },
    methods: {
        search: function() {
            console.log("ricerca")
        }
    },
    // props: {
    //     "titles": Array
    // }
}

</script>

<style lang="scss" scoped>
    header {
        background-image: linear-gradient(to top, rgba(255, 0, 0, 0), rgba($color: #000000, $alpha: 0.5));
        height: 80px;
        width: 100%;
        
        #container_navbar {
            width: 80%;
            margin: 0 auto;
            display: flex;
            flex-direction: row;
            align-items: center;
            justify-content: space-between;
            #show-searched {
                width: 250px;
                h2 {
                color: lightgrey;
                h6 {
                    color: grey;
                }
            }
            }
        }
        #searchbar {
            display: flex;
            align-items: center;
            input {
                width: 400px;
                height: 30px;
                padding: 10px;
                margin-right: 25px;
            }
            button {
                padding: 10px;
                text-transform: uppercase;
                font-weight: bold;
            }
        }
    }
    header:hover {
        background-image: linear-gradient(to top, rgba(255,0,0,0), rgba($color: #000000, $alpha: 0.8));
    }
</style>