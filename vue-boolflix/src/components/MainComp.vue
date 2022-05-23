<template>
<main>
    <h1>Ecco i titoli che hai chiesto:</h1>
    <div class="container">
        <div class="row">
            <MovieCard v-for="(el, i) in apiMovieArray" :key="`apiMovieArray${i}`" :el="el"/>
        </div>
        <div class="row">
            <SerialCard v-for="(el, i) in apiSerialArray" :key="`apiSerialArray${i}`" :el="el"/>
        </div>
    </div>
</main>
</template>

<script>
import MovieCard from './MovieCard.vue';
import SerialCard from './SerialCard.vue'

export default {
    components: {
        MovieCard,
        SerialCard,
    },
    props:{
        apiMovieArray: Array,
        apiSerialArray: Array,
    }

}
</script>

<style scoped lang="scss">
@import '../assets/style/vars';
main{
    color: white;
    background-color: $bg-black;
    min-height: calc(100vh - 75px);
    padding: 20px;
    .container{
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;

        .row{
            padding: 10px;
            width: 80%;
            height: 36vh;
            margin: 2vh 0;
            border: solid 2px $netflix-red ;

            display: flex;
            flex-direction: column;
            flex-wrap: wrap;
            overflow-x: scroll;
            justify-content: center;
            align-items: flex-start;
        }
    }
    h1{
        color: $netflix-red;
    }
}
</style>