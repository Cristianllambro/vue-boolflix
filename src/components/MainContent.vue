<template>
  <div class="container">
      <div class="main">
        <CardMovies v-for="element in arrMovies" :key="element.title" 
        :title="element.title"
        :origianlTitle="element.original_title"
        :lang="element.original_language"
        :vote="element.vote_average" />
      </div>
  </div>
</template>

<script>
import CardMovies from './CardMovies.vue'
import axios from 'axios';

export default {
    name: 'MainContent',
    components: {
        CardMovies,
    },

    props: {
        dataGenerate: String,
    },

    data () {
        return {
            arrMovies: [],
        }
    },

    methods: {
        movieResearch() {
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=3fb5afa145004592af904e3418c1b1f8&language=en-US&query=${this.dataGenerate}&page=1&include_adult=false`)
            .then ((itemResult) => {
                this.arrMovies = itemResult.data.results
                console.log(itemResult.data.results)
            });
        }
    },


}
</script>

<style lang="scss" scoped>
.container{
    width: 100vw;
    background-color: lightgray;
}
</style>