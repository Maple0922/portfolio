<template>
  <div class="portfolio__card" @click="showMore">
    <div class="portfolio__card__shadow">MORE</div>
    <div class="portfolio__card__top">
      <img
        class="portfolio__card__image"
        :src="require(`@/assets/images/photo/${portfolioItem.image}`)"
        :alt="portfolioItem.image"
      />
    </div>
    <div class="portfolio__card__bottom">
      <h4 class="portfolio__card__title">{{ portfolioItem.title }}</h4>
      <p class="portfolio__card__description">
        {{ portfolioItem.description }}
      </p>
      <p class="portfolio__card__used">
        使用技術:
        <span
          class="portfolio__card__used__item"
          v-for="(tech, key) in portfolioItem.used"
          :key="key"
          >{{ tech }}</span
        >
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "PortfolioCard",
  props: ["portfolioItem"],

  methods: {
    showMore() {
      this.$emit("showMore", this.portfolioItem);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";

.portfolio {
  &__card {
    background: transparentize($white, 0.4);
    border-radius: 4px;
    box-shadow: 0 1px 3px 0px $light-gray;
    position: relative;
    transition: 0.3s;
    cursor: pointer;
    @include mq("pc") {
      height: 500px;
      width: calc(33.3% - 30px);
      margin: 0 15px 30px;
      &:last-child {
        margin-bottom: 80px;
      }
    }
    @include mq("tab") {
      width: calc(50% - 30px);
      height: 500px;
    }
    @include mq("sp") {
      width: 100%;
      max-width: 400px;
      margin: 0 auto 30px;
      height: 460px;
    }

    &__shadow {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: #002c;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 24px;
      opacity: 0;
      transition: 0.3s;
      z-index: 1000;
      color: $white;
      border-radius: 4px;
    }

    &__top {
      height: 240px;
      width: 100%;
      border-radius: 4px 4px 0 0;
      border-bottom: 1px solid $super-light-gray;
      overflow: hidden;
    }

    &__image {
      height: 240px;
      width: 100%;
      object-fit: cover;
      transition: 0.3s;
    }

    &__bottom {
      padding: 16px 0;
    }

    &__title {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 10px;
      padding: 0 20px;
    }

    &__description {
      padding-bottom: 20px;
      display: block;
      padding: 0 10px 10px;
      margin: 0 10px;
      margin-bottom: 10px;
      border-bottom: 1px solid $light-gray;
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 12.8px;
      }
    }

    &__used {
      padding: 0 20px;
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 12px;
      }

      &__item {
        display: inline-block;
        margin: 0 4px;
        padding: 2px 6px;
        background: $super-light-gray;
        border-radius: 4px;
        text-align: center;
      }
    }
    &:hover {
      opacity: 0.6;
      .portfolio__card__shadow {
        opacity: 1;
      }
      .portfolio__card__image {
        transform: scale(1.1);
      }
    }
  }
}
</style>
