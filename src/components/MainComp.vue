<template>
  <main>
     <div class="main-container">
       <div class="title-box">Risultati per: "{{ query }}"</div>
      <card-comp v-for="item in mResults.results" :item="item" :key="item.id"/> 
    </div>
  </main>
</template>

<script>
import CardComp from './CardComp.vue'

export default {
  name: 'MainComp', 
  components:{
    CardComp
  },
  props:{
    mResults: Object,
    query: String
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
    padding: 0 20px;
    color: rgb(201, 201, 201);
  }
</style>
