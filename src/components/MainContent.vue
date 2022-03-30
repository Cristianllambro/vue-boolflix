<template>
  <div class="container">

        <h2>MOVIE</h2>

        <!-- card movie -->
        <div class="movie">
            <card-movies v-for="element in arrMovies" :key="element.id"
                :img="element.poster_path" 
                :title="element.title"
                :origianlTitle="element.original_title"
                :lang="element.original_language"
                :vote="element.vote_average" 
            />
        </div>

        <h2>TV SHOW</h2>

        <!-- card tv-show -->
        <div class="series-tv">
            <card-show v-for="element in arrShow" :key="element.id"
                :img="element.poster_path"
                :titleShow="element.name"
                :originalShowTitle="element.original_name"
                :langShow="element.original_language"
                :voteShow="element.vote_everage"
            />
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

}
</script>

<style lang="scss" scoped>
.container{
    width: 100vw;
    background-color: lightgray;
}
</style>