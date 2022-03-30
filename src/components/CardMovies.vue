<template>
  <div class="card">
      <img :src="imgUrl + img" :alt="title" v-if="img !== null">
      <h2> Title: {{ title }}</h2>
      <h2>Original Title: {{origianlTitle }}</h2>
      <h2> Rating: 
          <span v-for="(element,index) in 5" :key="index" :class="index < ratingNumber() ? 'red' : '' ">&starf;</span>
      </h2>

      <h3>
        Lenguage: <lang-flag :iso="lang" :squared="false" />
      </h3>
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
            imgUrl: 'https://image.tmdb.org/t/p/w300',
        }
    },

    methods: {
        // function for retaing number;
        ratingNumber() {
            let rating;

            if(this.vote !== 0) {
                rating = Math.ceil(this.vote / 2)
            } else {
                rating = 0;
            }
            return rating
        },
    }
}
</script>

<style lang="scss">
.card{
    width: 400px;
    padding: 2rem 2rem;
    color: white;
}

.red{
    color: crimson;
}
</style>