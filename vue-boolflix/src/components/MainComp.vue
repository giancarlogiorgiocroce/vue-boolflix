<template>
<main>
    <div class="container">
        <div class="row" v-if="apiMovieArray.length == 0 || apiSerialArray.length == 0">
            <h1>I più visti su Boolflix:</h1>
            <div class="slider trending">
                <CardComp v-for="(el, i) in apiTrendingArray" :key="`apiTrendingArray${i}`" :el="el"/>
            </div>
        </div>

        <div class="row" v-if="apiMovieArray.length > 0">
            <h1>Ecco i film che hai chiesto:</h1>
            <div class="slider films">
                <CardComp v-for="(el, i) in apiMovieArray" :key="`apiMovieArray${i}`" :el="el"/>
            </div>
        </div>

        <div class="row" v-if="apiSerialArray.length > 0">
            <h1>Ecco le serie che hai chiesto:</h1>
            <div class="slider serial">
                <CardComp v-for="(el, i) in apiSerialArray" :key="`apiSerialArray${i}`" :el="el"/>
            </div>
        </div>
    </div>
</main>
</template>

<script>
import CardComp from './CardComp.vue';

export default {
    components: {
        CardComp,
    },
    props:{
        apiMovieArray: Array,
        apiSerialArray: Array,
        apiTrendingArray: Array,
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
    overflow-x: scroll;
    .container{
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        flex-wrap: wrap;
        h1{
            color: $netflix-red;
            margin: 25px 0;
        }
        .slider{
            width: 100%;
            height: 45%;
            display: flex;
        }
    }
}
</style>