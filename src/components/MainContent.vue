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


export default {
    name: 'MainContent',
    components: {
        CardMovies,
    },

    props: {
        movieResearch: String,
    },

    data () {
        return {
            arrMovies: [],
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