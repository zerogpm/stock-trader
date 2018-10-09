<template>
    <div class="col-sm-6 col-md-4">
        <div class="panel panel-success">
            <div class="panel-heading">
                <h3 class="panel-title">
                    {{ option.name }}
                    <small>(Price: {{ option.price | currency }} | Quantity: {{ option.quantity }})</small>
                </h3>
            </div>
            <div class="panel-body">
                <div class="pull-left">
                    <input
                            type="number"
                            class="form-control"
                            placeholder="Quantity"
                            v-model.number="quantity"
                    >
                </div>

                <div class="pull-right">
                    <button
                            class="btn btn-success"
                            @click="sellStock"
                            :disabled="insufficientQuantity || quantity <= 0 || !Number.isInteger(quantity)"
                    >
                        {{ insufficientQuantity ? 'insuffice quantity' : 'Sell' }}
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
    computed: {
      insufficientQuantity () {
        return this.quantity > this.option.quantity
      }
    },
    methods: {
      ...mapActions({
        sellingStock: 'sellStock'
      }),
      sellStock() {
        const order = {
          stockId: this.option.id,
          stockPrice: this.option.price,
          quantity: this.quantity
        }
        this.sellingStock(order)
        this.quantity = 0
      }
    }
  }
</script>

<style scoped>

</style>
