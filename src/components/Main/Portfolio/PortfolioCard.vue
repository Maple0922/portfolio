<template>
  <div class="portfolio__card" @click="showMore">
    <div class="portfolio__card__shadow">MORE</div>
    <div class="portfolio__card__top">
      <img
        class="portfolio__card__image"
        :src="require(`@/assets/images/photo/${portfolioItem.thumbnail}`)"
        :alt="portfolioItem.thumbnail"
      />
    </div>
    <div class="portfolio__card__bottom">
      <h4 class="portfolio__card__title">{{ portfolioItem.title }}</h4>
      <span class="portfolio__card__date">{{ portfolioItem.date }}</span>
      <p class="portfolio__card__description">
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
  // responsive
  &__card {
    @include mq("pc") {
      height: 500px;
      width: calc(33.3% - 30px);
      margin: 0 15px 30px;
    }
    @include mq("tab") {
      width: calc(33.3% - 30px);
      height: 400px;
    }
    @include mq("sp") {
      width: calc(50% - 24px);
      margin: 12px;
      height: 280px;
    }

    &__top {
      @include mq("pc") {
        height: 240px;
      }
      @include mq("tab") {
        height: 180px;
      }
      @include mq("sp") {
        height: 130px;
      }
    }
    &__bottom {
      @include mq("pc") {
        padding: 16px 0;
      }
      @include mq("tab") {
        padding: 12px 0;
      }
      @include mq("sp") {
        padding: 8px 0;
      }
    }
    &__title {
      @include mq("pc") {
        font-size: 18px;
        padding: 0 20px;
      }
      @include mq("tab") {
        padding: 0 16px;
        font-size: 15px;
      }
      @include mq("sp") {
        padding: 0 10px;
        font-size: 13px;
      }
    }
    &__date {
      @include mq("pc") {
        font-size: 14px;
        padding-right: 24px;
        margin-bottom: 6px;
      }
      @include mq("tab") {
        font-size: 12px;
        padding-right: 16px;
        margin-bottom: 6px;
      }
      @include mq("sp") {
        font-size: 10px;
        padding-right: 12px;
        margin-bottom: 6px;
      }
    }
    &__description {
      @include mq("pc") {
        font-size: 14px;
        padding: 0 20px;
      }
      @include mq("tab") {
        font-size: 12px;
        padding: 0 12px;
      }
      @include mq("sp") {
        display: none;
      }
    }
    &__border {
      @include mq("pc") {
        margin: 0 16px 16px;
      }

      @include mq("tab") {
        margin: 0 12px 8px;
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
      @include mq("tab") {
        padding: 0 12px;
        font-size: 12px;
      }
      @include mq("sp") {
        padding: 0 10px;
        font-size: 10px;
      }
    }
  }
  &__card {
    background: transparentize($white, 0.4);
    border-radius: 4px;
    box-shadow: 0 1px 3px 0px $light-gray;
    position: relative;
    transition: 0.3s;
    cursor: pointer;

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
      z-index: -1000;
      color: $white;
      border-radius: 4px;
    }

    &__top {
      width: 100%;
      border-radius: 4px 4px 0 0;
      border-bottom: 1px solid $super-light-gray;
      overflow: hidden;
    }

    &__image {
      height: 100%;
      width: 100%;
      object-fit: cover;
      transition: 0.3s;
    }

    &__title {
      font-weight: bold;
    }

    &__date {
      color: $light-gray;
      display: inline-block;
      width: 100%;
      text-align: right;
      line-height: 0.5;
      font-weight: bold;
    }

    &__description {
      margin-bottom: 10px;
    }

    &__used {
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
        z-index: 1000;
      }
      .portfolio__card__image {
        transform: scale(1.1);
      }
    }
  }
}
</style>
