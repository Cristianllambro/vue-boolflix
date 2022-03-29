<template>
  <div id="app">
    <HeaderContent @callSearch="movieResearch" />
    <MainContent :arrMovies = arrMovies :arrShow = arrShow />
  </div>
</template>

<script>
import HeaderContent from './components/HeaderContent.vue'
import MainContent from './components/MainContent.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HeaderContent,
    MainContent,
  },
  data () {
    return {
      arrMovies: [],
      arrShow: [],
    }
  },

  methods: {
    movieResearch(itemMovie) {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=3fb5afa145004592af904e3418c1b1f8&language=en-US&query=${itemMovie}&page=1&include_adult=false`)
      .then ((itemResult) => {
        console.log(itemResult.data.results)
        this.arrMovies = itemResult.data.results
      });

      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=3fb5afa145004592af904e3418c1b1f8&language=en-US&query=${itemMovie}&page=1&include_adult=false`)
        .then((itemShow) => {
        console.log(itemShow)
        this.arrShow = itemShow.data.results
      });
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;700&display=swap');
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}
</style>
