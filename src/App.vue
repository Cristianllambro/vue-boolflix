<template>
  <div id="app">
    <HeaderContent @callSearch="dataMovie" />
    <MainContent :dataGenerate = strGenerate />
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
      strGenerate: '',
    }
  },

  methods: {
    dataMovie(dataElement) {
      console.log(dataElement)
      this.strGenerate = dataElement
    },

    movieResearch() {
    axios.get(`https://api.themoviedb.org/3/search/movie?api_key=3fb5afa145004592af904e3418c1b1f8&language=en-US&query=${this.dataGenerate}&page=1&include_adult=false`)
    .then ((itemResult) => {
        this.arrMovies = itemResult.data.results
        console.log(itemResult.data.results)
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
