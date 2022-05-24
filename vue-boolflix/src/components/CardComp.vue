<template>

<div class="card-box">
    <div :class="(el.backdrop_path != null) ? `active` : `inactive`" class="image">
        <img :src="`https://image.tmdb.org/t/p/w342/${el.backdrop_path}`">
        <p>{{el.title || el.name}}</p>
    </div>

    <ul :class="(el.backdrop_path == null) ? `active` : `inactive`">
        <li>
            <span>Titolo italiano:</span>
            <div>{{el.title || el.name}}</div>
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
            <div class="stars"> 
                <i v-for="(str, i) in trasformIntoStars(el.vote_average)" :key="`starsArray${i}`" :class="`fa-${str} fa-star`"></i> 
            </div>
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
    methods:{
        trasformIntoStars(vote){
            const solid = 'solid';
            const regular = 'regular';
            const maxVote = 5;

            let starsArray = [];
            let numberOfFullStars = Math.floor(vote / 2);

            for(let i = 0; i < numberOfFullStars; i++){
                starsArray.push(solid);
            }
            for(let i = 0; i < maxVote-numberOfFullStars; i++){
                starsArray.push(regular);
            }
            
            return starsArray;
        }
    }

}
</script>

<style scoped lang="scss">
@import '../assets/style/vars';

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