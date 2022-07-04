<template>
  <li 
    class="order-card"
    @dragstart="onStartDrag($event, order.id)"
    draggable="true">
    <h3 class="order-card__title">Заказ #{{ order.id }}</h3>
    <p class="order-card__price">{{ order.total }} руб</p>
    <div 
      @click="showPopup" 
      class="order-card__more">
      <img 
        width="20" 
        src="../assets/icon/three-dots.png" 
        alt="подробнее">
    </div>
    <MorePopup 
      :isVisible="isVisiblePopup"
      :basketItems="order.basket_items"
      :changeVisibleModal="changeVisibleModal"
      :changeOrderItem="changeOrderItem"
      :orderId="order.id"
      :deleteOrderItem="deleteOrderItem"
      :moveOrderToShipment="moveOrderToShipment"/>
  </li>
</template>

<script>
  import MorePopup from './MorePopup.vue'

  export default {
    props: {
      order: {
        type: Object
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
    },
    components: {
      MorePopup
    },
    data: function() {
      return {
        isVisiblePopup: false
      }
    },
    methods: {
      showPopup: function() {
        this.isVisiblePopup = !this.isVisiblePopup
      }
    }
  }
</script>

<style>
  .order-card {
    border: 2px solid var(--font-default);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 20px;
    position: relative;
  }

  .order-card__title {
    font-size: 1.2rem;
  }

  .order-card__price {
    font-size: 1.2rem;
  }

  .order-card__more {
    border: 1px solid var(--font-default);
    padding: 5px;
    cursor: pointer;
  }
</style>