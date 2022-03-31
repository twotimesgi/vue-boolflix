<template>
  <main>
     <div class="main-container">
        <div v-if="query != ''" class="title-box">Films per: "{{ query }}"</div>
        <div v-else class="title-box">Film Popolari         <filter-comp @filter="mFilter" :collection="mGenres" /></div> 
        <card-comp v-show="item.genre_ids.includes(mCat) || mCat == '' " :mGenres = "mGenres" :sGenres = "sGenres" v-for="item in mResults.results" :item="item" :key="item.id"/> 
        <div v-if="query != ''" class="title-box">Serie TV per: "{{ query }}"</div>
        <div v-else class="title-box">Serie TV Popolari         <filter-comp @filter="sFilter" :collection="sGenres"/></div>
      <card-comp v-show="item.genre_ids.includes(sCat) || sCat == '' " :catFilter="sCat" :mGenres = "mGenres" :sGenres = "sGenres" v-for="item in sResults.results" :item="item" :key="item.id" />
     </div>
  </main>
</template>

<script> 
import CardComp from './CardComp.vue'
import FilterComp from './FilterComp.vue'

export default {
  name: 'MainComp', 
  components:{
    CardComp,
    FilterComp
  },
  props:{
    mResults: Object,
    sResults: Object,
    query: String,
    loaded: Boolean,
    mGenres: Array,
    sGenres: Array
  },
  data(){
    return {
      mCat: "",
      sCat: ""
    }
  },
  methods: {
    mFilter(mCat){
      this.mCat = mCat;
      console.log(mCat)
    },
    sFilter(sCat){
      this.sCat = sCat;
      console.log(sCat)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  .main-container{
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    width: 90%;
    justify-content: center;
    margin: 0 auto;
    padding: 30px 0;
  }
  
  .title-box{
    width: 100%;
    padding: 0 50px;
    color: rgb(201, 201, 201);
  }
</style>
