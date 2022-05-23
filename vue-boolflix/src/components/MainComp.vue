<template>
<main>
    <div class="container">
        <h1>Ecco i film che hai chiesto:</h1>
        <div class="row films">
            <CardComp v-for="(el, i) in apiMovieArray" :key="`apiMovieArray${i}`" :el="el"/>
        </div>
        <h1>Ecco le serie che hai chiesto:</h1>
        <div class="row serial">
            <CardComp v-for="(el, i) in apiSerialArray" :key="`apiSerialArray${i}`" :el="el"/>
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
    overflow: scroll;
    .container{
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        flex-wrap: wrap;
        h1{
            color: $netflix-red;
            margin: 3% 0 1% 0;
        }
        .row{
            width: 100%;
            height: 45%;
            display: flex;
        }
    }
}
</style>