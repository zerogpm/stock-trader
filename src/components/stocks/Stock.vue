<template>
    <div class="col-sm-6 col-md-4">
        <div class="panel panel-success">
            <div class="panel-heading">
                <h3 class="panel-title">
                    {{ option.name }}
                    <small>(Price: {{ option.price | currency }})</small>
                </h3>
            </div>
            <div class="panel-body">
                <div class="pull-left">
                    <input
                      type="number"
                      class="form-control"
                      placeholder="Quantity"
                      v-model.number="quantity"
                      :class="{danger: insufficientFunds}"
                    >
                </div>

                <div class="pull-right">
                    <button
                      class="btn btn-success"
                      @click="buyStock"
                      :disabled="insufficientFunds || quantity <= 0 || !Number.isInteger(quantity)"
                    >
                        {{ insufficientFunds ? 'Insufficient' : 'Buy' }}
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
  import { mapActions } from 'vuex'
  export default {
    props: ['option'],
    data () {
      return {
        quantity: 0
      }
    },
    computed : {
      funds() {
        return this.$store.getters.funds
      },
      insufficientFunds () {
        return this.quantity * this.option.price > this.funds
      }
    },
    methods: {
      ...mapActions({
        buyPersonalStock: 'buyStock'
      }),
      buyStock () {
        const order = {
          stockId: this.option.id,
          stockPrice: this.option.price,
          quantity: this.quantity
        }
        this.buyPersonalStock(order)
        this.quantity = 0
      }
    }
  }
</script>

<style scoped>
    .danger {
        border: 1px solid red;
    }
</style>
