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
      <span class="portfolio__card__date">{{ portfolioItem.date }}</span>
      <p class="portfolio__card__description" v-if="sp">
        {{ portfolioItem.description }}
      </p>
      <hr class="portfolio__card__border" />
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
import isMobile from "ismobilejs";

export default {
  name: "PortfolioCard",

  data() {
    return {
      isMobile,
    };
  },

  props: ["portfolioItem"],

  methods: {
    showMore() {
      this.$emit("showMore", this.portfolioItem);
    },
  },

  computed: {
    sp: function () {
      const userAgent = window.navigator;
      return this.isMobile(userAgent).any;
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
      width: calc(50% - 24px);
      margin: 12px;
      height: 280px;
      max-width: 200px;
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
      width: 100%;
      border-radius: 4px 4px 0 0;
      border-bottom: 1px solid $super-light-gray;
      overflow: hidden;
      @include mq("pc") {
        height: 240px;
      }
      @include mq("sp") {
        height: 130px;
      }
    }

    &__image {
      height: 100%;
      width: 100%;
      object-fit: cover;
      transition: 0.3s;
    }

    &__bottom {
      @include mq("pc") {
        padding: 16px 0;
      }
      @include mq("sp") {
        padding: 8px 0;
      }
    }

    &__title {
      font-weight: bold;
      @include mq("pc") {
        padding: 0 20px;
        font-size: 18px;
        margin-bottom: 6px;
      }
      @include mq("sp") {
        padding: 0 10px;
        font-size: 13px;
      }
    }

    &__date {
      color: $dark-gray;
      display: inline-block;
      width: 100%;
      text-align: right;
      line-height: 0.5;
      @include mq("pc") {
        font-size: 14px;
        padding-right: 24px;
        margin-bottom: 6px;
      }
      @include mq("sp") {
        font-size: 12px;
        padding-right: 12px;
        margin-bottom: 6px;
      }
    }

    &__description {
      padding-bottom: 20px;
      display: block;
      padding: 0 10px;
      margin: 0 10px;
      margin-bottom: 10px;
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 12.8px;
      }
    }

    &__border {
      @include mq("pc") {
        margin: 0 16px 16px;
      }
      @include mq("sp") {
        margin: 0 8px 8px;
      }
    }

    &__used {
      @include mq("pc") {
        padding: 0 20px;
        font-size: 14px;
      }
      @include mq("sp") {
        padding: 0 10px;
        font-size: 10px;
      }

      &__item {
        display: inline-block;
        margin: 0 2px;
        padding: 0 4px;
        background: $super-light-gray;
        border-radius: 3px;
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
