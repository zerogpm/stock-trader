<template>
  <div class="container">
    <app-header></app-header>
    <div class="row">
      <div class="col-xs-12">
        <router-view></router-view>
      </div>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header'
  import { mapActions } from 'vuex'
  export default {
    components: {
      appHeader: Header
    },
    methods: {
      ...mapActions({
        getStocks: 'loadStocks'
      })
    },
    created() {
      this.getStocks()
    }
  }
</script>

<style>
  body {
    padding: 30px;
  }
</style>
