<template>
  <div id="app">
    <HeaderComp @findMovieOrSerial="changeApiCall"/>
    <MainComp :apiArray="this.apiArray"/>
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
    this.callApi('Mad Max');
  },
  data(){
    return{
      /* Chiamata API */
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      /* /Chiamata API */

      apiArray: [],
    }
  },
  methods:{
    callApi(data){
      axios.get(this.apiUrl, {
        params:{
          api_key: "0fb42841a10eeeb72a511057dfcd693b",
          language: "it-IT",
          query: data,
        }
      })
      .then(res => {
        // console.log(res.data.results);
        this.apiArray = res.data.results;
      })
      .catch(err => {
        console.log(err);
      })
    },
    changeApiCall(str){
      // console.log(str, 'il passaggio sta funzionando');
      this.callApi(str);
    }
  }
}
</script>

<style lang="scss">
@import 'assets/style/_global.scss';
@import 'assets/style/_vars.scss';

</style>
