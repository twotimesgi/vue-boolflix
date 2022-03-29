<template>
  <header>
    <div class="header-container">
      <img class="logo" src="../assets/logo.png">
      <div class="filters">
        <input class="search-field" placeholder="Cerca..." type="text">
        <input class="search-btn" type="button" value="Cerca">
      </div>
    </div>
  </header>
</template>

<script>
export default {
   name: 'HeaderComp', 
  props: {
    msg: String
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

.search-field{
  height: 30px;
  margin-right: 20px;
  padding: 0 5px;
}

.search-btn{
  background-color: #db0000;
  border: none;
  height: 30px;
  color: white;
  padding: 0 25px;

  &:active{
    background-color: #831010;
  }
}

@media screen and (max-width: 600px){
  .header-container{
    flex-direction: column;
  }
}
</style>
