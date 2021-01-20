<template>
  <header class="header">
    <div class="header__container">
      <h1 class="header__title" :class="{ show: showTitle }">
        Futo Nakajima's Portfolio
      </h1>
      <p class="header__caption" :class="{ show: showCaption }">
        - Web Engineer -
      </p>
      <div class="header__links" :class="{ show: showLinks }">
        <a
          class="header__link"
          v-for="(link, key) in links"
          :key="key"
          :href="'#' + link.name.toLowerCase()"
          v-smooth-scroll
          >{{ link.name }}</a
        >
      </div>
    </div>
  </header>
</template>

<script>
import Vue from "vue";
import VueSmoothScroll from "vue-smooth-scroll";
Vue.use(VueSmoothScroll);

export default {
  name: "Header",
  data() {
    return {
      showTitle: false,
      showCaption: false,
      showLinks: false,
      links: [
        {
          name: "Profile",
        },
        {
          name: "Skills",
        },
        {
          name: "Portfolio",
        },
        {
          name: "Contact",
        },
      ],
    };
  },
  mounted() {
    setTimeout(() => {
      this.showTitle = true;
      setTimeout(() => {
        this.showCaption = true;
        setTimeout(() => {
          this.showLinks = true;
        }, 300);
      }, 300);
    }, 500);
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";

.header {
  position: relative;
  width: 100%;
  color: $header-text;
  background: url("../assets/images/photo/header.jpg");
  background-position: center 0%;
  background-size: cover;

  &__container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    vertical-align: center;
    background: $header-shadow;
  }

  &__title {
    margin-bottom: 10px;
    font-weight: 300;
    text-align: center;
  }

  &__caption {
    font-weight: 300;
    color: $caption-text;
    text-align: center;
  }

  &__link {
    color: $link-text;
    text-decoration: underline;
    display: inline-block;
    transition: 0.3s;
    @include mq("pc") {
      &:hover {
        color: lighten($link-text, 16);
      }
    }
  }

  &__title,
  &__caption,
  &__links {
    transition: 1s;
    transform: translateY(30px);
    opacity: 0;

    &.show {
      transform: translateY(0);
      opacity: 1;
    }
  }

  @include mq-header("sp") {
    height: $height-header-sp;

    &__title {
      font-size: 20px;
    }

    &__caption {
      font-size: 14px;
      margin-bottom: 20px;
    }

    &__link {
      font-size: 12px;
      margin: 0 6px;
    }
  }

  @include mq-header("tab") {
    height: $height-header-tab;

    &__title {
      font-size: 28px;
    }

    &__caption {
      font-size: 18px;
      margin-bottom: 30px;
    }

    &__link {
      margin: 0 6px;
      font-size: 16px;
    }
  }

  @include mq-header("pc") {
    height: $height-header-pc;

    &__title {
      font-size: 36px;
    }

    &__caption {
      font-size: 22px;
      margin-bottom: 40px;
    }

    &__link {
      font-size: 18px;
      margin: 0 12px;
    }
  }
}
</style>
