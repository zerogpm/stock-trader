<template>
    <div>
        <h1>The Stocks Component</h1>
        <app-stock v-for="stock in stockOptions" :option="stock"></app-stock>
    </div>
</template>

<script>
  import Stock from './Stock'
  export default {
    data () {
      return {
        stockOptions: [
          { id: 1, name: 'FaceBook', price: 110 },
          { id: 2, name: 'Google', price: 120 },
          { id: 3, name: 'Amazon', price: 140 },
          { id: 3, name: 'Apple', price: 140 }
        ]
      }
    },
    components: {
      appStock: Stock
    }
  }
</script>

<style scoped>

</style>
