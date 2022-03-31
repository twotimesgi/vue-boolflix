<template>
    <div class="search">
      <input class="search-field" placeholder="Cerca..."  v-model="query" type="text">
      <input class="btn" type="button" value="Cerca" @click="$emit('search', query)">
  </div>
</template> 

<script>
export default {
  name: 'SearchComp', 
  data(){
    return {
      query: "",
      menuOpened: false
    }
  },
  methods: {
    toggleMenu(){
      this.menuOpened = !this.menuOpened;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

.search{
    width: 100%;
    flex-grow: 1;
    display: flex;
    justify-content: flex-end;
}

.search-field{
  height: 30px;
  margin-right: 20px;
  padding: 0 5px;
  flex-flow: 100000;
}

.btn{
  height: 30px;
  border: none;
  background-color:#db0000;
  color: white;
  padding: 0 20px;
  margin-right: 10px;
  flex-grow: 1;
  max-width: 100px;

  &:active{
    background-color: #831010;
  }
}
@media screen and (max-width: 600px){
  .search{
    justify-content: center; 
  }
}
</style>
