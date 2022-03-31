<template>
    <div class="card">
        <img class="img" :src="imgUrl + img" :alt="titleShow" v-if="img !== null">
        <img class="img-color" src="../../public/img-color-2.jpg" alt="color" v-else>

        <!-- text for tv show -->
        <div class="visible-txt">
            <h2>Title: {{ titleShow }}</h2>
            <h2>Original Title: {{originalShowTitle }}</h2>
            <h2> Rating: 
                <span v-for="(element,index) in 5" :key="index" :class="index < ratingNumber() ? 'red' : '' ">&starf;</span>
            </h2>
            
            <h3>
                Lenguage: <lang-flag :iso="langShow" :squared="false" />
            </h3>
            <h4>Overview: {{ overview }}</h4>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'CardShow',

    components: {
        LangFlag,
    },

    props: {
        img: String,
        titleShow: String,
        originalShowTitle: String,
        langShow: String,
        voteShow: String,
        overview: String,
    },

    data () {
        return {
            imgUrl: 'https://image.tmdb.org/t/p/w342',
        }
    },

    methods: {
        // function for rating number
        ratingNumber() {
            let rating;

            if(this.voteShow !== 0) {
                rating = Math.ceil(this.voteShow / 2)
            } else {
                rating = 0;
            }
            return rating
        },
    }
}
</script>

<style>
.red{
    color: crimson;
}
.bk-color{
    background-color: aqua;
}

.img-color{
    width: 342px;
    height: 513px;
    object-fit: cover;
    border-radius: 10px;
}
</style>