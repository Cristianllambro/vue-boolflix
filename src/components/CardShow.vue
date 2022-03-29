<template>
    <div class="card">
        <h1>{{ titleShow }}</h1>
        <h2>{{originalShowTitle }}</h2>
        <lang-flag :iso="langShow" :squared="false" />
        <h2>{{ voteShow }}</h2>
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
        titleShow: String,
        originalShowTitle: String,
        langShow: String,
        voteShow: String,
    }
}
</script>

<style>

</style>