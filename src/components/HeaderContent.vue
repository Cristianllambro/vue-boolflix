<template>
  <div class="container">
    <div class="main-header">
        <div class="logo">
            <img class="img-logo" src="../../public/logo-netflix.png" alt="logo netflix">

            <ul>
                <li><a href="#!">Home</a></li>
                <li><a href="#!">Movies</a></li>
                <li><a href="#!">TV Show</a></li>
            </ul>

        </div>


        <form class="search" @submit.prevent="">
            <input class="input" type="text" placeholder="Search movie" v-model="inputMovie">
            <button class="btn" @click="$emit('callSearch', inputMovie), clearInput()">Search</button>
        </form>
    </div>
  </div>
</template>

<script>
export default {
    name: 'HeaderContent',
    data () {
        return {
            inputMovie: '',
        }
    },

    methods: {
        clearInput() {
            this.inputMovie = '';
        }
    }
}
</script>

<style lang="scss" scoped>
.container{
    max-width: 99vw;
    height: 100px;
    background-color: black;
}

.main-header{
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: space-between;

    .img-logo{
        width: 220px;
        height: 100px;
        display: inline-block;
    }

    .logo{
        width: 700px;
        color: red;
        padding-left: 2rem;
        cursor: pointer;
        display: flex;
        align-items: center;

        li{
            list-style: none;
            display: inline-block;
            padding: 0 1rem;

            a{
                text-decoration: none;
                color: white;
            }
        }
    }
    
    .search{
        padding-right: 2rem;

        .input{
            padding: .7rem .3rem;
            border-radius: 5px;
            border: none;
        }

        .btn{
            color: white;
            background-color: red;

            padding: .7rem;
            margin-left: 1rem;

            border-radius: 5px;
            border: none;
            cursor: pointer;
        }
    }
}

</style>