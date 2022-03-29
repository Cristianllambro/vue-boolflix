<template>
  <div class="card">
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
        title: String,
        origianlTitle: String,
        lang: String,
        vote: Number,
    },
    components: {
        LangFlag,
  },
}
</script>

<style lang="scss" scoped>
.card{
    padding: 2rem 2rem;
}
</style>