<template>
  <transition>
    <div class="hamburger-menu" v-if="isActive">
      <ul class="menu">
        <li class="menu__item" v-for="(menu, key) in menus" :key="key">
          <a
            :href="'#' + menu.enName.toLowerCase()"
            @click="close"
            v-smooth-scroll
          >
            <h4 class="menu__title">{{ menu.enName }}</h4>
            <p class="menu__description">{{ menu.jaName }}</p>
          </a>
        </li>
      </ul>
      <div class="sns">
        <!-- <a
          class="sns__link"
          href="https://twitter.com/Fool_Maple"
          rel="noreferrer"
          target="_blank"
        >
          <component class="sns__icon twitter" :is="'TwitterSvg'" />
        </a> -->
        <a
          class="sns__link"
          href="https://github.com/Maple0922"
          rel="noreferrer"
          target="_blank"
        >
          <component class="sns__icon github" :is="'GithubWhiteSvg'" />
        </a>
      </div>
    </div>
  </transition>
</template>

<script>
import Vue from "vue";
import VueSmoothScroll from "vue-smooth-scroll";
// import TwitterSvg from "@/assets/images/svg/twitter.svg";
import GithubWhiteSvg from "@/assets/images/svg/github_white.svg";
Vue.use(VueSmoothScroll);

export default {
  name: "HamburgerMenu",
  data() {
    return {
      menus: [
        {
          enName: "Profile",
          jaName: "プロフィール",
        },
        {
          enName: "Skills",
          jaName: "スキル",
        },
        {
          enName: "Portfolio",
          jaName: "制作実績",
        },
        {
          enName: "Contact",
          jaName: "お問い合わせ",
        },
      ],
    };
  },
  methods: {
    close() {
      this.$parent.isActiveMenu = false;
    },
  },
  props: {
    isActive: Boolean,
  },

  components: {
    // TwitterSvg,
    GithubWhiteSvg,
  },
};
</script>

<style lang="scss">
@import "@/assets/scss/import";
@import "@/assets/scss/reset";

.v-leave-active,
.v-enter-active {
  transition: opacity 0.2s;
}
.v-enter,
.v-leave-to {
  opacity: 0;
}

.hamburger-menu {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 3000;
  padding: 90px 0;
  color: $white;
  background: #111111f3;
  text-align: left;

  .menu {
    width: 240px;
    margin: 0 auto 60px;

    &__item {
      margin-bottom: 36px;

      a {
        transition: 0.3s;

        @include mq("pc") {
          &:hover {
            color: blue;
          }
        }
      }
    }

    &__title {
      margin-bottom: 8px;
      transition: 0.2s;
    }

    &__description {
      color: $gray;

      &::before {
        margin-right: 8px;
        content: "−";
      }
    }

    @include mq("pc") {
      &__title {
        font-size: 28px;
      }

      &__description {
        font-size: 16px;
      }
    }

    @include mq("tab") {
      &__title {
        font-size: 24px;
      }

      &__description {
        font-size: 14px;
      }
    }

    @include mq("sp") {
      &__title {
        font-size: 20px;
      }

      &__description {
        font-size: 14px;
      }
    }
  }

  .sns {
    display: flex;
    justify-content: space-around;
    width: 240px;
    margin: 0 auto;

    &__link {
      transition: 0.3s;

      @include mq("pc") {
        &:hover {
          opacity: 0.6;
        }
      }
    }

    &__icon {
      @include mq("pc") {
        width: 64px;
        height: 64px;
      }

      @include mq("sp") {
        width: 48px;
        height: 48px;
      }
    }
  }
}
</style>
