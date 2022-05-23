<template>
  <div id="app">
    <HeaderComp @findMovieOrSerial="changeApiCall"/>
    <MainComp :apiMovieArray="this.apiMovieArray" :apiSerialArray="this.apiSerialArray"/>
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
    this.callMovieApi('Mad Max');
  },
  data(){
    return{
      /* Chiamata API */
      apiMovieUrl: 'https://api.themoviedb.org/3/search/movie',
      apiSerialUrl: 'https://api.themoviedb.org/3/search/tv',
      /* /Chiamata API */

      apiMovieArray: [],
      apiSerialArray: [],
    }
  },
  methods:{

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
    }
  }
}
</script>

<style lang="scss">
@import 'assets/style/_global.scss';
@import 'assets/style/_vars.scss';

</style>
