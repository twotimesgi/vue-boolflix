<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img class="cover"
          v-if="item.poster_path != null"
          :src="'https://image.tmdb.org/t/p/w500' + item.poster_path"
        />
      </div>
      <div class="flip-card-back">
        <div><span>Titolo: </span> {{ item.title }}</div>
        <div v-if="item.original_title != item.title">
          <span>Titolo originale: </span> {{ item.original_title }}
        </div>
        <div>
          <span>Lingua originale: </span>
          <img
            class="flag"
            :src="
              'https://flagcdn.com/w20/' +
              getCountryCode(item.original_language) +
              '.png'
            "
          />
        </div>
        <div><span>Voto: </span>{{ item.vote_average }}</div>
        <div v-if="item.overview != ''">
          <span>Overview: </span>{{ item.overview }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardComp",
  props: {
    item: Object,
  },
  methods: {
    getCountryCode(lang){
      switch (lang) {
        case 'en':
          return "us";
        case 'ja':
          return "jp";
        case 'ko':
          return "kr";
        case "zh":
          return 'cn';
        default:
          return lang;
    }
  }
},
};
</script>
<style lang="scss" scoped>
.flip-card {
  background-color: transparent;
  width: 300px;
  height: 400px;
  border: 1px solid #8f8f8f;
  perspective: 1000px;
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
</style>
