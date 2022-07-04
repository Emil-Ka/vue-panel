<template>
  <HeaderBlock
    :changeTheme="changeTheme"/>
  <MainBlock
    :orders="orders"
    :deliveries="deliveries"
    :changeVisibleModal="changeVisibleModal"
    :changeOrderItem="changeOrderItem"
    :deleteOrderItem="deleteOrderItem"
    :moveOrderToShipment="moveOrderToShipment"
    :deleteShipmentItem="deleteShipmentItem"
    :updateOrder="updateOrder"
    :updateShipment="updateShipment"
    :onStartDrag="onStartDrag"
    :onDrop="onDrop"/>
  <FooterBlock/>
  <ModalWindow
    :orderItem="orderItem"
    :visibleModal="visibleModal"
    :changeVisibleModal="changeVisibleModal"
    :deleteOrderItem="deleteOrderItem"
    :moveOrderToShipment="moveOrderToShipment"/>
</template>

<script>
  import MainBlock from './components/MainBlock.vue'
  import HeaderBlock from './components/HeaderBlock.vue'
  import FooterBlock from './components/FooterBlock.vue'
  import ModalWindow from './components/ModalWindow.vue'

  export default {
    components: {
      MainBlock,
      HeaderBlock,
      FooterBlock,
      ModalWindow
    },
    data() {
      return {
        orders: [],
        deliveries: [],
        visibleModal: false,
        orderItem: {},
        theme: 'light'
      }
    },
    methods: {
      changeOrderItem(id) {
        this.orderItem = this.orders.filter(item => item.id == id)[0]
        this.updateOrder()
      },

      changeVisibleModal() {
        this.visibleModal = !this.visibleModal
      },

      deleteOrderItem(id) {
        fetch(`https://demo-api.vsdev.space/api/orders_admin/0599/orders/${id}`, {
          method: 'DELETE'
        })
        .then(this.updateOrder())
      },

      deleteShipmentItem(id) {
        fetch(`https://demo-api.vsdev.space/api/orders_admin/0599/deliveries/${id}`, {
          method: 'DELETE'
        })
        .then(this.updateShipment())
      },

      moveOrderToShipment(id) {
        fetch(`https://demo-api.vsdev.space/api/orders_admin/0599/orders/${id}`, {
          method: 'DELETE'
        })
        .then(this.updateOrder())
        fetch(`https://demo-api.vsdev.space/api/orders_admin/0599/orders/${id}/delivery`, {
          method: 'POST',
          body: JSON.stringify({
            order_id: id
          })
        })
        .then(this.updateShipment())
      },

      updateOrder() {
        fetch('https://demo-api.vsdev.space/api/orders_admin/0599/orders')
          .then(response => response.json())
          .then(response => {
            this.orders = response
          })
          .catch(err => console.error(err))
      },

      updateShipment() {
        fetch('https://demo-api.vsdev.space/api/orders_admin/0599/deliveries')
          .then(response => response.json())
          .then(response => {
            this.deliveries = response
          })
          .catch(err => console.error(err))
      },

      onStartDrag(event, orderId) {
        event.dataTransfer.dropEffect = 'move'
        event.dataTransfer.effectAllowed = 'move'
        event.dataTransfer.setData('orderId', orderId)
      },

      onDrop(event) {
        const orderId = event.dataTransfer.getData('orderId')
        this.moveOrderToShipment(orderId)
      },

      changeTheme() {
        const newTheme = this.theme === 'light' ? 'dark' : 'light'
        this.theme = newTheme

        const root = document.querySelector(':root')
        const components = ['bg', 'font']

        components.forEach(component => {
          root.style.setProperty(`--${component}-default`, `var(--${component}-${newTheme})`)
        })
      }
    },
    mounted() {
      this.updateOrder()
      this.updateShipment()
    }
  }
</script>

<style>
  html {
    font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
    color: var(--font-default);
  }

  body {
    background: var(--bg-default);
    display: flex;
    flex-direction: column;
    margin: 0;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
  }

  #app {
    display: flex;
    flex-direction: column;
    position: relative;
  }

  :root {
  --bg-light: #fff;
  --bg-dark: #0D1117;

  --font-light: #000;
  --font-dark: #fff;

  --font-grey: #939393;
  --font-green: #00c632;
  --font-red: #c10000;

  --bg-default: var(--bg-light);
  --font-default: var(--font-light);
  }
</style>
