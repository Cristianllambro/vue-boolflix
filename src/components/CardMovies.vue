<template>
  <div class="card">
      <h1>{{ title }}</h1>
      <h2>{{origianlTitle }}</h2>
      <h2>{{ lang }}</h2>
      <h2>{{ vote }}</h2>
  </div>
</template>

<script>
export default {
    name: 'CardMovies',
    props: {
        title: String,
        origianlTitle: String,
        lang: String,
        vote: Number,
    }
}
</script>

<style lang="scss" scoped>
.card{
    padding: 2rem 2rem;
}
</style>