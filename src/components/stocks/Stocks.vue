<template>
    <div>
        <h1>The Stocks Component</h1>
        <app-stock v-for="stock in stockOptions" :option="stock"></app-stock>
    </div>
</template>

<script>
  import Stock from './Stock'
  export default {
    components: {
      appStock: Stock
    },
    computed: {
      stockOptions () {
        return this.$store.getters.stocks
      }
    },
    mounted() {
      console.log(this.$store.getters.stocks)
    }
  }
</script>

<style scoped>

</style>
