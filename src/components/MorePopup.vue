<template>
  <ul v-bind:class="{popup_active: isVisible, popup_hidden: !isVisible}">
    <li 
      class="popup__item"
      @click="changeOrderItem(orderId); changeVisibleModal()">
      <button class="popup__btn">Подробнее</button>
    </li>
    <li class="popup__item">
      <button 
        class="popup__btn popup__btn--green"
        @click="moveOrderToShipment(orderId)">К отгрузке</button>
    </li>
    <li class="popup__item">
      <button 
        class="popup__btn popup__btn--red"
        @click="deleteOrderItem(orderId)">Отменить</button>
    </li>
  </ul>
</template>

<script>
  export default {
    props: {
      isVisible: {
        type: Boolean
      },
      basketItems: {
        type: Array
      },
      changeVisibleModal: {
        type: Function
      },
      changeOrderItem: {
        type: Function
      },
      orderId: {
        type: Number
      },
      deleteOrderItem: {
        type: Function
      },
      moveOrderToShipment: {
        type: Function
      },
    }
  }
</script>

<style>
  .popup_hidden {
    display: none;
  }

  .popup_active {
    position: absolute;
    z-index: 2;
    right: -90px;
    top: 20px;
    padding: 0;
    font-family: "Helvetica Neue",Helvetica;
    list-style: none;
    max-width: 110px;
    margin: 0;
    background: #fff;
  }

  .popup__item {
    border: 1px solid var(--font-default);
    background: var(--bg-default);
    padding: 5px;
    margin: 0 !important;
  }

  .popup__btn {
    color: var(--font-default);
    background: var(--bg-default);
    border: none;
    cursor: pointer;
    font-size: 1rem;
    margin: 0;
  }

  .popup__btn--green {
    color: var(--font-green);
  }

  .popup__btn--red {
    color: var(--font-red);
  }
</style>