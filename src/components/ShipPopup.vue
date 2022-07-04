<template>
  <ul v-bind:class="{popup_active: isVisiblePopup, popup_hidden: !isVisiblePopup}">
    <li class="popup__item">
      <button 
        @click="deleteShipmentItem(deliveryId)"
        class="popup__btn popup__btn--red">Отменить</button>
    </li>
  </ul>
</template>

<script>
  export default {
    props: {
      isVisiblePopup: {
        type: Boolean
      },
      deleteShipmentItem: {
        type: Function
      },
      deliveryId: {
        type: Number
      }
    }
  }
</script>