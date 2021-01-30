<template>
  <div class="portfolio__dialog" @click="closeDialog">
    <div class="portfolio__dialog__container">
      <div class="portfolio__dialog__top"></div>
      <p class="portfolio__dialog__title">{{ portfolioItem.title }}</p>
      <p class="portfolio__dialog__description">
        {{ portfolioItem.description }}
        {{ portfolioItem.supplement }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "PortfolioDialog",
  props: ["portfolioItem"],

  methods: {
    closeDialog() {
      this.$parent.showMoreDialog = false;
    },
  },
};
</script>



<style lang="scss" scoped>
@import "@/assets/scss/import";

.portfolio__dialog {
  width: 100%;
  height: 100vh;
  position: fixed;
  display: flex;
  align-items: center;
  top: 0;
  left: 0;
  background: #0009;
  opacity: 0;
  transition: 0.3s;
  pointer-events: none;

  &--show {
    opacity: 1;
    pointer-events: all;
  }

  &__container {
    max-width: 1000px;
    width: 84%;
    margin: 0 auto;
    background: $main-background;
    border-radius: 4px;

    @include mq("pc") {
      padding: 24px 16px;
    }
    @include mq("sp") {
      padding: 24px 16px;
    }
  }

  &__title {
    font-size: 20px;
    font-weight: bold;
  }
}
</style>
