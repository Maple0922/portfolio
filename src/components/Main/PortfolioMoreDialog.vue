<template>
  <div class="portfolio__dialog" @click="closeDialog">
    <div class="portfolio__dialog__container">
      <div class="portfolio__dialog__images">
        <div class="portfolio__dialog__images__show">
          <img
            class="portfolio__dialog__images__show__item"
            :src="require(`@/assets/images/photo/${portfolioItem.thumbnail}`)"
            :alt="portfolioItem.thumbnail"
          />
        </div>
        <div class="portfolio__dialog__images__list">
          <img
            class="portfolio__dialog__images__list__item"
            v-for="(image, key) in portfolioItem.images"
            :src="require(`@/assets/images/photo/${image}`)"
            :alt="image"
            :key="key"
          />
        </div>
      </div>
      <div class="portfolio__dialog__contents">
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
  </div>
</template>

<script>
export default {
  name: "PortfolioMoreDialog",
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
      display: flex;
      justify-content: center;
    }
    @include mq("sp") {
      padding: 12px 16px;
    }
  }

  &__images {
    display: block;
    border: 1px solid black;
    @include mq("pc") {
      width: 50%;
    }
    @include mq("sp") {
      width: 100%;
    }

    &__show {
      width: 100%;
      &__item {
        width: 100%;
        object-fit: cover;
        @include mq("pc") {
          height: 400px;
        }
        @include mq("sp") {
          height: 200px;
        }
      }
    }

    &__list {
      width: 100%;
      &__item {
        width: 33%;
        height: 133px;
        object-fit: cover;
      }
    }
  }

  &__contents {
    border: 1px solid black;
    @include mq("pc") {
      width: 50%;
    }
    @include mq("sp") {
      width: 100%;
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
