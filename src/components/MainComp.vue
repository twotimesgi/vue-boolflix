<template>
  <main>
    <div class="main-container">
      <card-comp v-for="item in movieResults.results" :item="item" :key="item.id"/> 
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
    movieResults: Object
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
</style>
