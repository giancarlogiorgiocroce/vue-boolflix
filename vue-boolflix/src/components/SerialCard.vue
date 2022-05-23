<template>
<div class="box">
    <div :class="(el.backdrop_path != null) ? `active` : `inactive`" class="img">
        <img :src="`https://image.tmdb.org/t/p/w342/${el.backdrop_path}`">
        <p>{{el.name}}</p>
    </div>

    <ul :class="(el.backdrop_path == null) ? `active` : `inactive`">
        <li>
            <span>Titolo italiano:</span>
            {{el.name}}
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
</div>

</template>

<script>
import CountryFlag from 'vue-country-flag';

export default {
    components:{
        CountryFlag,
    },
    props:{
        el: Object,
    },

}
</script>

<style scoped lang="scss">
.box{
    width: 342px;
    height: 192px;
    margin: 0 10px;
    position: relative;
    &:hover ul{
        visibility: visible;
    }
    &:hover .img{
        visibility: hidden;
    }
}
.img{
    position: relative;

    p{
        position: absolute;
        left: 5px;
        bottom: 5px;
        background: black;
    }
}
ul{
    overflow-y: auto;
    visibility: hidden;

    span{
        color: grey;
    }
    div.lang{
        display: inline;
        margin-left: 10px;
    }
}
ul,
.img{
    position: absolute;
    width: 100%;
    height: 100%;
}
.active{
    visibility: visible;
}
.inactive{
    visibility: hidden;
}
</style>