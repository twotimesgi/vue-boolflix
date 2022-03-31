<template>
      <select v-model="currFilter" @change="$emit('filter', currFilter)">
        <option value="">All</option>
        <option v-for="item in collection" :key="item.id" :value="item.id">{{ item.name }}</option>
      </select>
</template> 

<script>
export default {
  name: 'FilterComp',
  props: {
    collection: Array
  },
  data(){
    return {
      currFilter: ""
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
