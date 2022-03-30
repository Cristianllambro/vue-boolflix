<template>
  <div class="container">
      <div class="visible">
           <!-- card movie -->
        <h2>MOVIE</h2>

        <div class="item">
            <card-movies v-for="element in arrMovies" :key="element.id"
                :img="element.poster_path" 
                :title="element.title"
                :origianlTitle="element.original_title"
                :lang="element.original_language"
                :vote="element.vote_average" 
            />
        </div>

        <!-- card tv-show -->
        <h2 class="help">TV SHOW</h2>

        <div class="item">
            <card-show v-for="element in arrShow" :key="element.id"
                :img="element.poster_path"
                :titleShow="element.name"
                :originalShowTitle="element.original_name"
                :langShow="element.original_language"
                :voteShow="element.vote_average"
            />
        </div>
      </div>
       

        <div class="home-movie">
            <div class="card" v-for="element in arrHomeMovies" :key="element.id"></div>
        </div>
  </div>
</template>

<script>
import CardMovies from './CardMovies.vue'
import CardShow from './CardShow.vue'
import axios from 'axios'

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

    created () {
        axios.get("https://api.themoviedb.org/3/movie/{movie_id}/lists?api_key=3fb5afa145004592af904e3418c1b1f8&language=en-US&page=1")
        .then ((item) => {
            this.arrHomeMovies = item.data.results
        })
    }

}
</script>

<style lang="scss" scoped>
.container{
    width: 100vw;
    background-color: #0f0f0f;
    h2{
        padding: 2rem 2rem;
        color: red;
        text-align: center;
    }

    .item{
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .help{
        padding: 4rem;
    }
}
</style>