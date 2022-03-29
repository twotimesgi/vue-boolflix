<template>
  <div id="app">
    <header-comp @search="search"/>
    <main-comp :movieResults="movieResults"/>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'
import Axios from "axios"

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data(){
    return {  
      movieResults: {},
    }
  },
  mounted(){
    this.search(null);
  },
  methods:{
    search(query){
      let query_url;
      query == null ? query_url = "https://api.themoviedb.org/3/discover/movie?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&sort_by=popularity.desc" : query_url = "https://api.themoviedb.org/3/search/movie?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&language=it-IT&include_adult=false&query="+query;
      Axios.get(query_url).then((response) => {
      this.movieResults = response.data;
    });
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: #564D4D;
  font-family: 'Roboto', sans-serif;
}
</style>
