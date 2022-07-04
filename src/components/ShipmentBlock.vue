<template>
  <section class="shipment">
    <div class="shipment__top">
      <div 
        class="shipment__refresh"
        @click="updateShipment()">
        <img width="20" src="../assets/icon/refresh.png" alt="перезагрузить">
      </div>
      <h2 class="shipment__title">Отгрузки</h2>
    </div>
    <ShipmentList 
      :deliveries='deliveries'
      :deleteShipmentItem="deleteShipmentItem"
      :onDrop="onDrop"/>
  </section>
</template>

<script>
  import ShipmentList from './ShipmentList.vue'

  export default {
    components: {
      ShipmentList
    },
    props: {
      deliveries: {
        type: Array
      },
      updateShipment: {
        type: Function
      },
      deleteShipmentItem: {
        type: Function
      },
      onDrop: {
        type: Function
      }
    }
  }
</script>

<style>
  .shipment {
    border: 2px solid var(--font-default);
    width: 100%;
    padding: 10px 15px;
  }

  .shipment__top {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    margin-bottom: 30px;
  }

  .shipment__title {
    font-size: 1.5rem;
  }

  .shipment__refresh {
    border: 1px solid var(--font-default);
    padding: 5px;
    position: absolute;
    left: 2%;
    cursor: pointer;
  }
</style>