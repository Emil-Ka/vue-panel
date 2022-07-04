<template>
  <footer>
    <div class="container">
      <div class="about">
        <p class="about__title">Караев Эмиль рафаилович 211-321</p>
        <a href="#main" class="about__arrow">
          <img width="40" src="../assets/icon/arrow-up.png" alt="наверх">
        </a>
      </div>
    </div>
  </footer>
</template>

<script>
  export default {}
</script>

<style>
  footer {
    margin-top: 20px;
  }

  .about {
    border: 2px solid var(--font-default);
    padding: 10px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
  }

  .about__title {
    font-size: 1.2rem;
  }

  .about__arrow {
    display: block;
    padding: 5px;
  }
</style>