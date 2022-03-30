<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img class="cover"
          v-if="item.poster_path != null"
          :src="'https://image.tmdb.org/t/p/w500' + item.poster_path"
        />
        <div v-else>
          <div class="circ">!</div>
          <div class="title">{{ item.title }}</div>  
        </div>
      </div>
      <div class="flip-card-back">
        <div><span>Titolo: </span> {{ item.origin_country ? item.name : item.title}}</div>
        <div v-if="item.original_title != item.title">
          <span>Titolo originale: </span> {{ item.original_title }}
        </div>
        <div>
          <span>Lingua originale: </span>
          <img v-if="langToCountryCode(item.original_language).res"
            class="flag"
            :src="
              'https://flagcdn.com/w20/' +
              langToCountryCode(item.original_language).text +
              '.png'
            "
          />
          <span v-else>{{ langToCountryCode(item.original_language).text }}</span>
        </div>
        <div><span>Voto: </span>
        <span v-for="i in Math.ceil(item.vote_average / 2)" :key="i">&#9733;</span>
        <span v-for="i in 5 - Math.ceil(item.vote_average / 2)" :key="i+5">&#9734;</span>
        </div>
        <div v-if="cast.length > 0"><span>Cast: </span><ul><li v-for="i in cast" :key="i.id"> {{ i.name }}</li></ul>
        </div>
        <div v-if="item.overview != ''">
          <span>Overview: </span>{{ item.overview }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Axios from "axios";

export default {
  name: "CardComp",
  props: {
    item: Object,
  },
  data(){
    return {
      cast: null
    }
  },
  created(){
    this.getCast(this.item);
  },
  methods: {
    langToCountryCode(lang){
      switch (lang) {
        case 'en':
          return {res: true, text: "us"};
        case 'ja':
          return {res: true, text: "jp"};
        case 'ko':
          return {res: true, text: "kr"};
        case "zh":
          return {res: true, text: "cn"};
        case "da":
          return {res: true, text: "dk"};
        case "hi":
          return {res: true, text: "in"};
        case "el":
          return {res: true, text: "gr"};
        case "cs":
          return {res: true, text: "cz"};
        case "uk":
          return {res: true, text: "gb"};
        case "it":
          return {res: true, text: "it"};
        case "fr":
          return {res: true, text: "fr"};
        case "pt":
          return {res: true, text: "pt"};
        case "es":
          return {res: true, text: "es"};
        case "sv":
          return {res: true, text: "se"};
        default:
          return {res: false, text: lang};
      }
    },
    getCast(item){
      let query;
      // se ha questa prop. è una serie
      item.origin_country ? query = "https://api.themoviedb.org/3/tv/"+item.id+"/credits?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&language=en-US" : query = "https://api.themoviedb.org/3/movie/"+item.id+"/credits?api_key=4ebc0e330e97f1a5c5b347b8ac63bdbb&language=en-US";
      Axios.request(query).then((resp)=>{
        this.cast = resp.data.cast.splice(0,5);
      });
    }
  }
};
</script>
<style lang="scss" scoped>
.star{
  width: 15px;
}
.flip-card {
  background-color: transparent;
  width: 300px;
  height: 400px;
  border: 1px solid #8f8f8f;
  perspective: 1000px;
}

ul{
  list-style: none;
}
.flip-card .cover {
  width: 100%;
  height: 100%;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: rgb(0, 0, 0);
  color: black;
}

.flip-card-back {
  background-color: rgb(0, 0, 0);
  color: white;
  transform: rotateY(180deg);
  padding: 20px;
  overflow-y: scroll;
}

.flip-card-back div {
  margin-bottom: 10px;
}

.flip-card-back span {
  font-weight: 800;
}

.flag{
  width: 20px;
}

.flip-card-front .circ{
  width: 100px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  height: 100px;
  background-color: white;
  opacity: 0.5;
  border-radius: 50%;
  line-height: 6.5rem;
  font-size: 5rem;
  text-align: center;
}

.title{
  color: white;
  width: 90%;
  margin: 10px auto;
  text-align: center;
}

</style>
