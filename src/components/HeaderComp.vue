<template>
  <header>
    <img class="logo" src="../assets/logo.png">
    <div class="filters"></div>
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
  height: 80px;
  width: :;
}
</style>
