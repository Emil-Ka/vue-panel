<template>
  <ul 
    class="shipment__content"
    @drop="onDrop($event)"
    @dragover.prevent
    @dragenter.prevent>
    <ShipmentCard
      :deleteShipmentItem="deleteShipmentItem"
      v-for='delivery in deliveries'
      :delivery = 'delivery'
      :key='delivery.id'/>
  </ul>
</template>

<script>
  import ShipmentCard from './ShipmentCard.vue'

  export default {
    components: {
      ShipmentCard
    },
    props: {
      deliveries: {
        type: Array
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
  .shipment__content li:not(:last-child) {
    margin-bottom: 20px;
  }
</style>