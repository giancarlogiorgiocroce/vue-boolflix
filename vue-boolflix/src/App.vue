<template>
  <div id="app">
    <HeaderComp @findMovieOrSerial="changeApiCall"/>
    <MainComp :movie="this.movie" :tv="this.tv" :apiTrendingArray="this.apiTrendingArray"/>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  mounted(){
    this.callTrendingApi();
  },
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiTrendingUrl: 'https://api.themoviedb.org/3/movie/popular',

      movie: [],
      tv: [],
      apiTrendingArray: []
    }
  },
  methods:{

    callApi(data, type){
      axios.get(this.apiUrl + type, {
        params:{
          api_key: "0fb42841a10eeeb72a511057dfcd693b",
          language: "it-IT",
          query: data,
        }
      })
      .then(res => {
        this[type] = res.data.results;
      })
      .catch(err => {
        console.log(err);
      })
    },
    
    changeApiCall(str){
      this.callApi(str, 'movie');
      this.callApi(str, 'tv');
    },

    callTrendingApi(){
      axios.get(this.apiTrendingUrl, {
        params:{
          api_key: "0fb42841a10eeeb72a511057dfcd693b",
          language: "it-IT",
        }
      })
      .then(response => {
        this.apiTrendingArray = response.data.results;
      })
      .catch(error => {
        console.log(error);
      })
    },
  }
}
</script>

<style lang="scss">
@import 'assets/style/_global.scss';
@import 'assets/style/_vars.scss';

</style>