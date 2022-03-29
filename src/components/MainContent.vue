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
const axios = require('axios');

export default {
    name: 'MainContent',
    components: {
        CardMovies,
    },

    data () {
        return {
            arrMovies: '',
        }
    },

    created () {
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=3fb5afa145004592af904e3418c1b1f8&query=ritorno+al+futuro').then ((result) => {
            this.arrMovies = result.data.results
            console.log(result)
        });
    },


}
</script>

<style lang="scss" scoped>
.container{
    width: 100vw;
    background-color: lightgray;
}
</style>