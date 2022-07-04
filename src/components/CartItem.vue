<template>
  <li class="modal__item">
    <h4 class="modal__product-name">{{ cartItem.name }}</h4>
    <span class="modal__count">{{ cartItem.quantity }}</span>
    <span class="modal__price">{{ cartItem.price }} руб</span>
  </li>
</template>

<script>
  export default {
    props: {
      cartItem: {
        type: Object
      }
    }
  }
</script>