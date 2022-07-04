<template>
  <main>
    <div class="container">
      <OrdersBlock 
        :orders="orders"
        :changeVisibleModal="changeVisibleModal"
        :changeOrderItem="changeOrderItem"
        :updateOrder="updateOrder"
        :deleteOrderItem="deleteOrderItem"
        :moveOrderToShipment="moveOrderToShipment"
        :onStartDrag="onStartDrag"/>
      <ShipmentBlock
        :deliveries="deliveries"
        :updateShipment="updateShipment"
        :deleteShipmentItem="deleteShipmentItem"
        :onDrop="onDrop"/>
    </div>
  </main>
</template>

<script>
  import OrdersBlock from './OrdersBlock.vue'
  import ShipmentBlock from './ShipmentBlock.vue'

  export default {
    components: {
      OrdersBlock,
      ShipmentBlock
    },
    props: {
      orders: {
        type: Array
      },
      deliveries: {
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
      deleteShipmentItem: {
        type: Function
      },
      updateOrder: {
        type: Function
      },
      updateShipment: {
        type: Function
      },
      onStartDrag: {
        type: Function
      },
      onDrop: {
        type: Function
      }
    }
  }
</script>

<style>
  main {
    flex-grow: 1;
  }

  main .container {
    display: flex;
    justify-content: space-between;
    column-gap: 20px;
  }
</style>