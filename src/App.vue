<template>
  <div id="app">
    <header-comp />
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue'

export default {
  name: 'App',
  components: {
    HeaderComp
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: #564D4D;
}
</style>
