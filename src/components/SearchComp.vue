<template>
    <div class="search">
      <input class="search-field" placeholder="Cerca..." @input="$emit('search', query)" v-model="query" type="text">
  </div>
</template> 

<script>
export default {
  name: 'SearchComp', 
  data(){
    return {
      query: ""
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

.search{
    width: 100%;
    max-width: 300px;
    flex-grow: 1;
}
.search-field{
  height: 30px;
  margin-right: 20px;
  padding: 0 5px;
  width: 100%;
  max-width: 300px;
}

@media screen and (max-width: 600px){
  .header-container{
    flex-direction: column;
  }
}
</style>
