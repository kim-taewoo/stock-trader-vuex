<template lang="html">
  <div class="col-sm-6 col-md-4">
    <div class="panel panel-success">
      <div class="panel-heading">
        <h3 class="panel-title">
          {{stock.name}}
          <small>(Price: {{stock.price}})</small>
        </h3>
      </div>
      <div class="panel-body">
        <div class="pull-left">
          <input
            type="number"
            class="form-control"
            placeholder="Quantity"
            v-model.number="quantity">
            <!-- input 은 type 를 "number" 로 해놓아도 string 을 반환하기에.. v-model.number 로 number를 강제해주는 게 필요하다.  -->
        </div>
        <div class="pull-right">
          <button @click="buyStock" :disabled="quantity < 0 || !Number.isInteger(quantity)" class="btn btn-success" name="button">Buy</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:['stock'],
  data() {
    return{
      quantity: 0
    }
  },
  methods: {
    buyStock() {
      const order= {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      };
      console.log(order);
      this.quantity = 0;
    }
  }
}
</script>

<style lang="css">
</style>
