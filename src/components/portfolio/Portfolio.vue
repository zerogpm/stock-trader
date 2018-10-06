<template>
    <div>
        <h1>Portfolio</h1>
        <app-stock v-for="stock in portfolioStocks" :option="stock"></app-stock>
    </div>
</template>

<script>
  import Stock from './Stock'
  import { mapGetters } from 'vuex'
  export default {
    computed: {
      ...mapGetters({
        portfolioStocks: 'stockPortfolio'
      })
    },
    components: {
      appStock: Stock
    }
  }
</script>

<style scoped>

</style>
