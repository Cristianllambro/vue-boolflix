<template>
  <div class="container">
    <div class="main-header">
        <div class="logo">
            BOOLFLIX
        </div>

        <form class="search" @submit.prevent="">
            <input class="input" type="text" placeholder="Search movie" v-model="inputMovie" @keyup.enter="$emit('callSearch', inputMovie)">
            <button class="btn" @click="$emit('callSearch', nameMovie)">Search</button>
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
    }
}
</script>

<style lang="scss" scoped>
.container{
    width: 100vw;
    height: 120px;
    background-color: black;
}

.main-header{
    width: 100vw;
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: space-between;

    .logo{
        font-size: 24px;
        font-weight: 700;
        color: red;
        padding-left: 2rem;
        cursor: pointer;
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