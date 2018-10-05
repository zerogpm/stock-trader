<template>
    <div>
        <h1>The Stocks Component</h1>
        <app-stock v-for="stock in stockOptions" :option="stock"></app-stock>
    </div>
</template>

<script>
  import Stock from './Stock'
  import { mapGetters } from 'vuex'
  export default {
    components: {
      appStock: Stock
    },
    computed: {
      ...mapGetters({
        stockOptions : 'stocks'
      })
    }
  }
</script>

<style scoped>

</style>
