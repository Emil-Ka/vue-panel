<template>
  <section class="orders">
    <div class="orders__top">
      <h2 class="orders__title">Заказы</h2>
      <div 
        class="orders__refresh"
        @click="updateOrder()">
        <img width="20" src="../assets/icon/refresh.png" alt="перезагрузить">
      </div>
    </div>
    <OrderList 
      :deleteOrderItem="deleteOrderItem"
      :moveOrderToShipment="moveOrderToShipment"
      :changeVisibleModal="changeVisibleModal"
      :changeOrderItem="changeOrderItem"
      :orders="orders"
      :onStartDrag="onStartDrag"/>
  </section>
</template>

<script>
  import OrderList from './OrderList.vue'
  
  export default {
    components: {
      OrderList
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
      updateOrder: {
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
  .orders {
    border: 2px solid var(--font-default);
    width: 100%;
    padding: 10px 15px;
  }

  .orders__top {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    margin-bottom: 30px;
  }

  .orders__title {
    font-size: 1.5rem;
  }

  .orders__refresh {
    border: 1px solid var(--font-default);
    padding: 5px;
    position: absolute;
    right: 2%;
    cursor: pointer;
  }
</style>