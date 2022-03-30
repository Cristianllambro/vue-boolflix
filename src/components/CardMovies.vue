<template>
  <div class="card">
      <img :src="imgUrl + img" :alt="title">
      <h1>{{ title }}</h1>
      <h2>{{origianlTitle }}</h2>
      <lang-flag :iso="lang" :squared="false" />
      <h2>{{ vote }}</h2>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'CardMovies',
    props: {
        img: String,
        title: String,
        origianlTitle: String,
        lang: String,
        vote: Number,
    },
    components: {
        LangFlag,
    },

    data () {
        return{ 
            imgUrl: 'https://image.tmdb.org/t/p/w342'
        }
    },

    methods: {
        ratingNumber() {
            let rating = parseInt(this.vote) 
        }
    }
}
</script>

<style lang="scss" scoped>
.card{
    padding: 2rem 2rem;
}
</style>