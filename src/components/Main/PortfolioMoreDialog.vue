<template>
  <div class="portfolio__dialog" @click="closeDialog">
    <div class="portfolio__dialog__container">
      <div class="portfolio__dialog__top"></div>
      <p class="portfolio__dialog__title">{{ portfolioItem.title }}</p>
      <div class="portfolio__dialog__content">
        <p class="portfolio__dialog__content__description">
          {{ portfolioItem.description }}
        </p>
        <p
          class="portfolio__dialog__content__supplement"
          v-for="(sup, key) in portfolioItem.supplement"
          :key="key"
        >
          {{ sup }}
        </p>
      </div>
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
  transition: 0.2s;
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
      padding: 16px 20px;
    }
    @include mq("sp") {
      padding: 12px 16px;
    }
  }

  &__title {
    font-weight: bold;
    @include mq("pc") {
      font-size: 20px;
      margin-bottom: 16px;
    }
    @include mq("sp") {
      font-size: 16px;
      margin-bottom: 12px;
    }
  }

  &__content {
    &__description {
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 10px;
      }
    }
    &__supplement {
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 10px;
      }
    }
  }
}
</style>
