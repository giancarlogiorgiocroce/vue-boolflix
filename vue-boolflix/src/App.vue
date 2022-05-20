<template>
  <div id="app">
    <HeaderComp />
    <MainComp />
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
    this.callApi();
  },
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      apiParams:{
        params:{
          api_key: "0fb42841a10eeeb72a511057dfcd693b",
          language: "it-IT",
          query: "Mad Max",
        }
      },
    }
  },
  methods:{
    callApi(){
      axios.get(this.apiUrl, this.apiParams)
      .then(res => {
        console.log(res.data.results);
      })
      .catch(err => {
        console.log(err);
      })
    }
  }
}
</script>

<style lang="scss">
@import 'assets/style/global';
@import 'assets/style/vars';

</style>
