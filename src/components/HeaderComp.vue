<template>
  <header>
    <div class="header-container">
      <img class="logo" src="../assets/logo.png">
      <search-comp @search="search"/>
    </div>
  </header>
</template>

<script>
import SearchComp from './SearchComp.vue';

export default {
  components: { SearchComp },
  name: 'HeaderComp', 
  methods: {
    search(query){
      this.$emit("search", query);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
header{
  width: 100%;
  background-color: #000000;
  padding: 20px 15px;
}

.header-container{
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100%;
  max-width: 900px;
  gap: 10px;
}

.logo{
  width: 150px;
}

@media screen and (max-width: 600px){
  .header-container{
    flex-direction: column;
    align-items: center;
  }
}
</style>
