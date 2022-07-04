<template>
  <header class="header">
    <div class="container">
      <h1 class="header__title">Название проекта</h1>
      <div class="header__theme-block theme-block">
        <span class="theme-block__title">Темная тема</span>
        <label class="theme-block__label">
          <input 
            type="checkbox" 
            name="theme"
            @change="changeTheme">
          <div class="marker"></div>
        </label>
      </div>
    </div>
  </header>
</template>

<style scoped>
  .header {
    margin-bottom: 20px;
  }

  .container {
    border: 2px solid var(--font-default);
    padding: 20px 0;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }

  .header__title {
    font-size: 2rem;
  }

  .header__theme-block {
    position: absolute;
    right: 2%;
  }

  .theme-block {
    display: flex;
    align-items: center;
  }

  .theme-block__title {
    font-size: 1.2rem;
    margin-right: 10px;
  }

  input {
    display: none;
  }

  input:checked + .marker { /*Стили для блока маркера*/
    background: #00539F;
  }

  input:checked + .marker:before { /*Стили для кружка внутри блока маркера*/
    left: calc(100% - 2px);
    transform: translateX(-100%);
  }

  .marker {
    cursor: pointer;
    width: 44px;
    height: 24px;
    background: #d1d1d1;
    border-radius: 60px;
    position: relative;
  }

  .marker:before { /*Сам круг*/
    content: '';
    position: absolute;
    left: 2px;
    top: 2px;
    bottom: 2px;
    width: 20px;
    height: 20px;
    background: #fff;
    border-radius: 50%;
    transition: 0.3s;
  }
</style>

<script>
  export default {
    props: {
      changeTheme: {
        type: Function
      }
    }
  }
</script>