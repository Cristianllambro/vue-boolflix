<template>
    <div class="container">

        <div class="enter" v-show="arrMovies == '' && arrShow == ''">
            <div class="welcome">
                <h1>CHOOSE YOUR MOVIE OR TV SHOW</h1>
            </div>
        </div>

        <!-- card movie -->
        <div>
            <h1 v-show="arrMovies!= ''">MOVIE</h1>

            <div class="item">
                <card-movies v-for="element in arrMovies" :key="element.id"
                    :img="element.poster_path" 
                    :title="element.title"
                    :origianlTitle="element.original_title"
                    :lang="element.original_language"
                    :vote="element.vote_average"
                    :overview="element.overview"
                />
            </div>
        </div>

            <!-- card tv-show -->
        <div v-show="arrShow != null">
            <h1 class="help" v-show="arrMovies!= ''">TV SHOW</h1>

            <div class="item">
                <card-show v-for="element in arrShow" :key="element.id"
                    :img="element.poster_path"
                    :titleShow="element.name"
                    :originalShowTitle="element.original_name"
                    :langShow="element.original_language"
                    :voteShow="element.vote_average"
                    :overview="element.overview"
                />
            </div>
        </div>
            
    </div>
</template>

<script>
import CardMovies from './CardMovies.vue'
import CardShow from './CardShow.vue'

export default {
    name: 'MainContent',
    components: {
        CardMovies,
        CardShow,
    },

    props: {
        arrMovies: Array,
        arrShow: Array,
    },

    data() {
        return {
            arrHomeMovies: ''
        };
    },
}
</script>

<style lang="scss" scoped>
.container{
    max-width: 99vw;
    background-color: #0f0f0f;

    .enter{
        height: calc(100vh - 100px);
    }

    h1{
        padding: 2rem 2rem;
        color: red;
        text-align: center;
    }

    .item{
        flex-basis: 100%;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 3rem;
    }

    .help{
        padding: 4rem;
    }
}
</style>