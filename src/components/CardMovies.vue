<template>
  <div class="card">
        <img class="img" :src="imgUrl + img" :alt="title" v-if="img !== null">
        <img class="img-color" src="../../public/img-color-2.jpg" alt="color" v-else>

        <!-- text for movie -->
        <div class="visible-txt">
            <h2> Title: {{ title }}</h2>
            <h2>Original Title: {{origianlTitle }}</h2>
            <h2> Rating: 
                <span v-for="(element,index) in 5" :key="index" :class="index < ratingNumber() ? 'red' : '' ">&starf;</span>
            </h2>

            <h3>
                Lenguage: <lang-flag :iso="lang" :squared="false" />
            </h3>
            <h4>Overview: {{ overview }}</h4>
        </div>
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
        overview: String,
    },
    components: {
        LangFlag,
    },

    data () {
        return{ 
            imgUrl: 'https://image.tmdb.org/t/p/w342',
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
    width: 342px;
    color: white;
    position: relative;
    cursor: pointer;
    .img{
        width: 342px;
        height: 513px;
        border-radius: 10px;
        object-fit: cover;

    }

    .visible-txt{
        width: 342px;
        height: 513px;
        background-color: black;
        border-radius: 10px;

        opacity: 0;
        padding: 1.3rem 1.3rem;
        position: absolute;
        top: 0;
        left: 0;

         overflow-y: auto;

        h2{
            padding-bottom: .6rem;
        }
        h3{
            padding-bottom: .6rem;
        }
        p{
            font-weight: bold;
        }
    }

    &:hover .img{
        transition: all 1.5s linear;
        opacity: 0;
    }

    &:hover .visible-txt{
        transition: all 1.5s linear;
        opacity: 1;
    }
}

.red{
    color: crimson;
}
</style>