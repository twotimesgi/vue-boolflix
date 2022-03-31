<template>
  <div id="app">
    <header-comp @search="search" />
    <main-comp :query="query" :mGenres = "mGenres" :sGenres = "sGenres" :loaded="loaded" :sResults ="sResults" :mResults="mResults"/>
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
      mResults: {},
      sResults: {},
      query: "",
      loaded: false,
      sGenres: [],
      mGenres: [],
    }
  },
  mounted(){
    this.search("");
    this.getGenres();
  },
  methods:{
    searchMovies(query){
      let query_url;
      query == "" ? query_url = "https://api.themoviedb.org/3/discover/movie?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&sort_by=popularity.desc" : query_url = "https://api.themoviedb.org/3/search/movie?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&language=it-IT&include_adult=false&query="+query;
      Axios.get(query_url).then((response) => {
      this.mResults = response.data;
      this.query = query;
    });
    },
    searchSeries(query){
      let query_url;
      query == "" ? query_url = "https://api.themoviedb.org/3/discover/tv?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&sort_by=popularity.desc" : query_url = "https://api.themoviedb.org/3/search/tv?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&language=it-IT&include_adult=false&query="+query;
      Axios.get(query_url).then((response) => {
      this.sResults = response.data;
      this.query = query;
    });
  },
  search(query){
    this.searchMovies(query);
    this.searchSeries(query);
  },
  getGenres(){
    Axios.get("https://api.themoviedb.org/3/genre/tv/list?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&language=it-IT").then((resp)=>{
      this.sGenres = resp.data.genres;
    });
    Axios.get("https://api.themoviedb.org/3/genre/movie/list?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&language=it-IT").then((resp)=>{
      this.mGenres = resp.data.genres;
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
