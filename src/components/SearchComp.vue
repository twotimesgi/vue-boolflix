<template>
    <div class="search">
      <input class="search-field" placeholder="Cerca..."  v-model="query" type="text">
      <input class="btn" type="button" value="Cerca" @click="$emit('search', query)">
      <div class="btn-menu">
        <input class="btn" type="button" value="Filtri" @click="toggleMenu">
        <div :class="menuOpened ? 'show' : ''" class="filters-menu">
            asdsd
        </div>
      </div>

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
.btn-menu{
  position: relative;
}

.btn-menu .btn::after{
  content: '\2304';
  display: block;
}

.filters-menu{
  background-color: black;
  width: 400px;
  height: 400px;
  border: 1px solid white;
  display: none;
  position: absolute;
  top:  30px;
  z-index: 100;
  right: 10px;
}

.filters-menu.show{
  display: block;
}
</style>
