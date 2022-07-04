<template>
  <div :class="{'dark-side': visibleModal, 'dark-side_hidden': !visibleModal}">
    <div class="modal">
      <div class="modal__top">
        <h3 class="modal__title">Заказ #{{ orderItem.id }}</h3>
        <button 
          class="modal__close"
          @click="changeVisibleModal">
          <img width="20" src="../assets/icon/cross.png" alt="close"/>
        </button>
      </div>
      <h2 class="modal__cart-title">Корзина</h2>
      <ul class="modal__list">
        <CartItem 
          v-for='cartItem in orderItem.basket_items'
          :cartItem='cartItem'
          :key='cartItem.name' />
      </ul>
      <div class="modal__total">
        <span class="modal__total-price">Итого: {{ orderItem.total }}</span>
      </div>
      <div class="modal__btns">
        <button 
          class="modal__btn modal__btn--green"
          @click="moveOrderToShipment(orderItem.id)">К отгрузке</button>
        <button 
          class="modal__btn modal__btn--red"
          @click="deleteOrderItem(orderItem.id)">Отменить</button>
      </div>
    </div>
  </div>
</template>

<script>
  import CartItem from './CartItem.vue'

  export default {
    components: {
      CartItem
    },
    props: {
      orderItem: {
        type: Object
      },
      visibleModal: {
        type: Boolean
      },
      changeVisibleModal: {
        type: Function
      },
      deleteOrderItem: {
        type: Function
      },
      moveOrderToShipment: {
        type: Function
      }
    }
  }
</script>

<style>
  .dark-side {
    position: fixed;
    z-index: 2;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.4);
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .dark-side_hidden {
    display: none;
  }

  .modal {
    font-family: "Helvetica Neue", Helvetica;
    margin: 0 auto;
    border: 2px solid var(--font-default);
    padding: 20px;
    background: var(--bg-default);
  }

  .modal__top {
    position: relative;
  }

  .modal__title {
    text-align: center;
    color: var(--font-default);
  }

  .modal__cart-title {
    font-size: 1.3rem;
    margin-bottom: 10px;
    margin: 0;
  }

  .modal__close {
    display: block;
    position: absolute;
    right: 0;
    background: none;
    border: 1px solid var(--font-default);
    padding: 4px;
    cursor: pointer;
  }

  .modal__list {
    list-style: none;
    padding: 0;
  }

  .modal__item {
    border: 1px solid var(--font-default);
    padding: 15px 10px;
    display: flex;
    justify-content: space-between;
    gap: 40px;
    align-items: center;
    margin-bottom: 20px;
  }

  .modal__product-name, .modal__count, .modal__price, .modal__total-price {
    color: var(--font-default);
    font-size: 1.2rem;
    margin: 0;
  }

  .modal__total {
    display: flex;
    justify-content: end;
    margin-bottom: 20px;
  }

  .modal__btns {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .modal__btn {
    border: 1px solid var(--font-default);
    background: var(--bg-default);
    display: block;
    padding: 8px;
    cursor: pointer;
  }

  .modal__btn--green {
    color: var(--font-green);
  }

  .modal__btn--red {
    color: var(--font-red);
  }
</style>