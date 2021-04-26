<template>
  <footer class="footer">
    <div class="footer__container">
      <small>©︎ 2020-{{ new Date().getFullYear() }} Futo Nakajima</small>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style lang="scss" scoped>
.footer {
  &__container {
    text-align: center;
    background: #2c3e50;
    color: white;
    font-weight: bold;
    padding: 4px 0;
  }
}
</style>
