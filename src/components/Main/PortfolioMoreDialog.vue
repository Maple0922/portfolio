<template>
  <div class="portfolio__dialog" @click="closeDialog">
    <div class="portfolio__dialog__container">
      <div class="portfolio__dialog__images">
        <div class="portfolio__dialog__images__show">
          <img
            class="portfolio__dialog__images__show__item"
            :src="withImage.thumbnail"
            :alt="portfolioItem.thumbnail"
          />
        </div>
        <div class="portfolio__dialog__images__list">
          <img
            class="portfolio__dialog__images__list__item"
            v-for="(image, key) in portfolioItem.images"
            :src="getImagePath(image)"
            :alt="image"
            :key="key"
          />
        </div>
      </div>
      <div class="portfolio__dialog__text">
        <p class="portfolio__dialog__title">{{ portfolioItem.title }}</p>
        <span class="portfolio__dialog__date">{{ portfolioItem.date }}</span>
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
        <hr class="portfolio__dialog__border" />
        <div class="porfolio__dialog__info">
          <p class="portfolio__dialog__info__used">
            使用技術:
            <span
              class="portfolio__dialog__info__used__item"
              v-for="(tech, key) in portfolioItem.used"
              :key="key"
              >{{ tech }}</span
            >
          </p>
          <p
            class="portfolio__dialog__info__github"
            v-if="portfolioItem.github"
          >
            <a
              class="portfolio__dialog__info__github__link"
              :href="getGithubUrl(portfolioItem.github)"
              rel="noreferrer"
              target="_blank"
            >
              <component
                class="portfolio__dialog__info__github__icon"
                :is="'GithubBlackSvg'"
              />
            </a>
          </p>
          <p class="portfolio__dialog__info__note" v-if="!portfolioItem.github">
            ※画像はイメージです。
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import GithubBlackSvg from "@/assets/images/svg/github_black.svg";

export default {
  name: "PortfolioMoreDialog",
  props: ["portfolioItem"],

  methods: {
    closeDialog() {
      this.$parent.showMoreDialog = false;
    },
    getImagePath(imageName) {
      return require("@/assets/images/photo/" + imageName);
    },
    getGithubUrl(repoName) {
      return `https://github.com/Maple0922/${repoName}`;
    },
  },

  computed: {
    withImage() {
      return {
        thumbnail:
          this.portfolioItem.thumbnail &&
          require(`@/assets/images/photo/${this.portfolioItem.thumbnail}`),
      };
    },
  },

  components: {
    GithubBlackSvg,
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

  // common
  &__container {
    width: 84%;
    margin: 0 auto;
    background: $main-background;
    border-radius: 4px;
    display: flex;
    overflow: hidden;
  }
  &__images {
    display: block;
    font-size: 0;
    border-radius: 4px 4px 0 0;

    &__show {
      width: 100%;
      &__item {
        width: 100%;
        object-fit: cover;
        border-bottom: 1px solid $white;
      }
    }

    &__list {
      width: 100%;
      &__item {
        object-fit: cover;
        cursor: pointer;
        border: 3px solid $super-light-gray;
        &.selected {
          border: 3px solid orange;
        }
      }
    }
  }

  &__text {
    font-size: 0;
  }

  &__title {
    font-weight: bold;
  }

  &__date {
    color: $light-gray;
    display: inline-block;
    width: 100%;
    text-align: right;
    font-weight: bold;
  }

  &__border {
    width: 104%;
    transform: translateX(-2%);
  }

  &__info {
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
    &__github {
      width: 100%;
      text-align: right;
      &__link {
        width: 30px;
        height: 30px;
        display: inline-block;
      }
      &__icon {
        width: 100%;
        height: 100%;
      }
    }
    &__note {
      color: $gray;
      display: inline-block;
      width: 100%;
      text-align: right;
    }
  }

  // responsive
  &__container {
    @include mq("pc") {
      justify-content: center;
      flex-direction: row-reverse;
      max-width: 800px;
    }
    @include mq("sp") {
      flex-direction: column;
      max-width: 360px;
    }
  }

  &__images {
    @include mq("pc") {
      width: 50%;
      border-left: 1px solid $super-light-gray;
    }
    @include mq("sp") {
      width: 100%;
      border-top: 1px solid $super-light-gray;
    }

    &__show {
      &__item {
        @include mq("pc") {
          height: 42vw;
          max-height: 400px;
        }
        @include mq("sp") {
          height: 84vw;
          max-height: 360px;
        }
      }
    }

    &__list {
      &__item {
        @include mq("pc") {
          width: 80px;
          height: 80px;
        }
        @include mq("sp") {
          width: 60px;
          height: 60px;
        }
      }
    }
  }

  &__text {
    @include mq("pc") {
      padding: 16px 20px;
      width: 50%;
    }
    @include mq("sp") {
      width: 100%;
      padding: 12px 16px;
    }
  }

  &__title {
    @include mq("pc") {
      font-size: 20px;
    }
    @include mq("sp") {
      font-size: 16px;
    }
  }

  &__date {
    @include mq("pc") {
      font-size: 14px;
      padding-right: 6px;
      margin-bottom: 10px;
    }
    @include mq("sp") {
      font-size: 11px;
      margin-bottom: 4px;
      padding-right: 8px;
    }
  }

  &__content {
    @include mq("pc") {
      margin-bottom: 12px;
    }
    @include mq("sp") {
      margin-bottom: 10px;
    }
    &__description,
    &__supplement {
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 11px;
      }
    }
  }
  &__border {
    @include mq("pc") {
      margin-bottom: 12px;
    }
    @include mq("sp") {
      margin-bottom: 10px;
    }
  }
  &__info {
    &__used {
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 11px;
      }
    }
    &__github {
      &__link {
        @include mq("pc") {
          transition: 0.3s;
          &:hover {
            opacity: 0.6;
            transform: scale(1.1);
          }
        }
      }
    }
    &__note {
      @include mq("pc") {
        font-size: 13px;
      }
      @include mq("sp") {
        font-size: 10px;
      }
    }
  }
}
</style>
