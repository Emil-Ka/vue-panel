<template>
  <ul class="orders__content">
      <OrderCard 
        :deleteOrderItem="deleteOrderItem"
        :moveOrderToShipment="moveOrderToShipment"
        v-for='order in orders'
        :order='order'
        :key='order.id'
        :changeVisibleModal="changeVisibleModal"
        :changeOrderItem="changeOrderItem"
        :onStartDrag="onStartDrag"/>
  </ul>
</template>

<script>
  import OrderCard from './OrderCard.vue'

  export default {
    components: {
      OrderCard
    },
    props: {
      orders: {
        type: Array
      },
      changeVisibleModal: {
        type: Function
      },
      changeOrderItem: {
        type: Function
      },
      deleteOrderItem: {
        type: Function
      },
      moveOrderToShipment: {
        type: Function
      },
      onStartDrag: {
        type: Function
      }
    }
  }
</script>

<style>
  .orders__content li:not(:last-child) {
    margin-bottom: 20px;
  }
</style>