<template>
  <li class="shipment-card">
    <h3 class="shipment-card__title">Отгрузка #{{ delivery.id }}</h3>
    <p class="shipment-card__order">Заказ #{{ delivery.order_id }}</p>
    <p class="shipment-card__date">{{ delivery.delivery_date }}</p>
    <div 
      class="shipment-card__more"
      @click="showShipPopup">
      <img width="20" src="../assets/icon/three-dots.png" alt="подробнее">
    </div>
    <ShipPopup 
      :isVisiblePopup="isVisiblePopup"
      :deliveryId="deliveryId"
      :deleteShipmentItem="deleteShipmentItem"/>
  </li>
</template>

<script>
  import ShipPopup from './ShipPopup.vue'

  export default {
    components: {
      ShipPopup
    },
    props: {
      delivery: {
        type: Object
      },
      deleteShipmentItem: {
        type: Function
      }
    },
    data() {
      return {
        isVisiblePopup: false,
        deliveryId: this.delivery.id
      }
    },
    methods: {
      showShipPopup() {
        this.isVisiblePopup = !this.isVisiblePopup
      }
    }
  }
</script>

<style>
  .shipment-card {
    border: 2px solid var(--font-default);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 20px;
    position: relative;
  }

  .shipment-card__title {
    font-size: 1.2rem;
  }

  .shipment-card__date {
    font-size: 1.2rem;
  }

  .shipment-card__more {
    border: 1px solid var(--font-default);
    padding: 5px;
    cursor: pointer;
  }
</style>