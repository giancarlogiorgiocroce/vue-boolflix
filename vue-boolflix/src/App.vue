<template>
  <div id="app">
    <HeaderComp @findMovieOrSerial="changeApiCall"/>
    <MainComp :apiMovieArray="this.apiMovieArray" :apiSerialArray="this.apiSerialArray" :apiTrendingArray="this.apiTrendingArray"/>
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
      /* Chiamata API */
      apiMovieUrl: 'https://api.themoviedb.org/3/search/movie',
      apiSerialUrl: 'https://api.themoviedb.org/3/search/tv',
      apiTrendingUrl: 'https://api.themoviedb.org/3/movie/popular',
      // apiUrl: 'https://api.themoviedb.org/3/search/',
      /* /Chiamata API */

      apiMovieArray: [],
      apiSerialArray: [],
      apiTrendingArray: []
    }
  },
  methods:{

    callTrendingApi(){
      axios.get(this.apiTrendingUrl, {
        params:{
          api_key: "0fb42841a10eeeb72a511057dfcd693b",
          media_type: 'tv',
          time_window: 'week',
        }
      })
      .then(response => {
        this.apiTrendingArray = response.data.results;
      })
      .catch(error => {
        console.log(error);
      })
    },

    callMovieApi(data){
      axios.get(this.apiMovieUrl, {
        params:{
          api_key: "0fb42841a10eeeb72a511057dfcd693b",
          language: "it-IT",
          query: data,
        }
      })
      .then(res => {
        this.apiMovieArray = res.data.results;
      })
      .catch(err => {
        console.log(err);
      })
    },

    callSerialApi(data){
      axios.get(this.apiSerialUrl, {
        params:{
          api_key: "0fb42841a10eeeb72a511057dfcd693b",
          language: "it-IT",
          query: data,
        }
      })
      .then(r => {
        this.apiSerialArray = r.data.results;
      })
      .catch(e => {
        console.log(e);
      })
    },

    changeApiCall(str){
      this.callMovieApi(str);
      this.callSerialApi(str);
      // this.callApi(str, 'Serial');
      // this.callApi(str, 'Movie');
    }

    // callApi(data, type){
    //   axios.get(this.apiMovieUrl + type, {
    //     params:{
    //       api_key: "0fb42841a10eeeb72a511057dfcd693b",
    //       language: "it-IT",
    //       query: data,
    //     }
    //   })
    //   .then(res => {
    //     this[`api${type}Array`] = res.data.results;
    //   })
    //   .catch(err => {
    //     console.log(err);
    //   })
    // },
  }
}
</script>

<style lang="scss">
@import 'assets/style/_global.scss';
@import 'assets/style/_vars.scss';

</style>
