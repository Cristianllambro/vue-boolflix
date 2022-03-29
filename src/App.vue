<template>
  <div id="app">
    <HeaderContent @callSearch="dataMovie" />
    <MainContent />
  </div>
</template>

<script>
import HeaderContent from './components/HeaderContent.vue'
import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    HeaderContent,
    MainContent,
  },

  methods: {
    dataMovie(dataElement) {
      console.log(dataElement)
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
