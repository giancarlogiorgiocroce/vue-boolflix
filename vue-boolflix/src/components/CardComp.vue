<template>

<div class="card-box">
    <div :class="(el.backdrop_path != null) ? `active` : `inactive`" class="image">
        <img :src="`https://image.tmdb.org/t/p/w342/${el.backdrop_path}`">
        <p v-if="el.title != undefined">{{el.title}}</p>
        <p v-else>{{el.name}}</p>
    </div>

    <ul :class="(el.backdrop_path == null) ? `active` : `inactive`">
        <li>
            <span>Titolo italiano:</span>
            <div v-if="el.title != undefined">{{el.title}}</div>
            <div v-else>{{el.name}}</div>
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
            <div class="stars" v-if="parseInt(el.vote_average)/2 > 4"> <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i> </div>
            <div class="stars" v-else-if="parseInt(el.vote_average)/2 > 3"> <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i> </div>
            <div class="stars" v-else-if="parseInt(el.vote_average)/2 > 2"> <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> </div>
            <div class="stars" v-else-if="parseInt(el.vote_average)/2 > 1"> <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> </div>
            <div class="stars" v-else-if="parseInt(el.vote_average)/2 > 0"> <i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> </div>
            <div class="stars" v-else-if="parseInt(el.vote_average)/2 == 0"> <i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> </div>
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
div.card-box{
    min-width: 342px;
    min-height: 192px;

    position: relative;
    
    display: flex;
    justify-content: center;
    align-items: center;

    &:hover ul{
        visibility: visible;
    }
    &:hover .image{
        visibility: hidden;
    }
}
.image{
    p{
        position: absolute;
        left: 5px;
        bottom: 5px;
        padding: 2px;
        background-color: black;
    }
}
ul{
    position: absolute;
    left: 5%;
    list-style: none;
    visibility: hidden;
    li{
        margin: 5px;
        span{
            color: grey;
            margin-right: 5px;
        }
        div{
            display: inline;
        }
    }
}

.active{
    visibility: visible;
}
.inactive{
    visibility: hidden;
}
</style>