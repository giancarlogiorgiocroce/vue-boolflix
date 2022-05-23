<template>
<!-- <div>
    Ciao
</div> -->
<ul>
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
        <div class="lang" v-if="el.original_language === 'it'"> <country-flag country='it' size='small'/> </div>
        <div class="lang" v-else-if="el.original_language === 'en'"> <country-flag country='usa' size='small'/> </div>
        <div class="lang" v-else> {{el.original_language}} </div>   
    </li>
    <li>
        <span>Voto medio:</span>
        {{el.vote_average}}
    </li>
</ul>

</template>

<script>
import CountryFlag from 'vue-country-flag'

export default {
    components:{
        CountryFlag,
    },
    props:{
        el: Object,
    }

}
</script>

<style scoped lang="scss">
ul{
    margin: 1rem;
    border-bottom: .5px solid lightgrey;
    width: calc(50% - 2rem);

    span{
        color: grey;
    }
    div.lang{
        display: inline;
        margin-left: 10px;
    }
}
</style>