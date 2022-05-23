<template>
<main>
    <h1>Ecco i titoli che hai chiesto:</h1>
    <div class="container">
        <!-- <div class="row"> -->
            <MovieCard v-for="(el, i) in apiArray" :key="`apiArray${i}`" :el="el"/>
        <!-- </div> -->
    </div>
</main>
</template>

<script>
import MovieCard from './MovieCard.vue';

export default {
    components: {
        MovieCard,
    },
    props:{
        apiArray: Array,
    }

}
</script>

<style scoped lang="scss">
@import '../assets/style/vars';
main{
    color: white;
    background-color: $bg-black;
    height: calc(100vh - 75px);
    overflow-y: hidden;
    .container{
        height: 100%;
        display: flex;
        // flex-direction: column;
        flex-wrap: wrap;
        justify-content: flex-start;
    }
    h1{
        color: $netflix-red;
        margin-bottom: 1rem;
    }
}
</style>