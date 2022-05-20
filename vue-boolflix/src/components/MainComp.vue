<template>
<main>
    <h1>Ecco i titoli che hai chiesto:</h1>
    <div class="container">
        <ul v-for="(el, i) in apiArray" :key="`apiArray${i}`">
            <li>
                <span>Titolo italiano:</span>
                {{el.title}}
            </li>
            <li>
                <span>Titolo originale:</span>
                {{el.original_title}}
            </li>
            <li>
                <span>Lingua originale:</span>
                {{el.original_language}}
            </li>
            <li>
                <span>Voto medio:</span>
                {{el.vote_average}}
            </li>
        </ul>
    </div>
</main>
</template>

<script>
export default {
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
    height: 100vh;
    overflow-y: scroll;
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
ul{
    margin: 1rem;
    border-bottom: .5px solid lightgrey;
    width: calc(50% - 2rem);

    span{
        color: grey;
    }
}
</style>