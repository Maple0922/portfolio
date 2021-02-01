<template>
  <main class="main">
    <Profile />
    <Skills />
    <Portfolio @showMore="showMore" />
    <PortfolioMoreDialog
      :class="{ 'portfolio__dialog--show': showMoreDialog }"
      :portfolioItem="showItem"
    />
    <Contact />
  </main>
</template>

<script>
import Profile from "@/components/Main/Profile.vue";
import Skills from "@/components/Main/Skills.vue";
import Portfolio from "@/components/Main/Portfolio.vue";
import PortfolioMoreDialog from "@/components/Main/PortfolioMoreDialog";
import Contact from "@/components/Main/Contact.vue";

export default {
  name: "Main",

  data() {
    return {
      showItem: {},
      showMoreDialog: false,
    };
  },

  methods: {
    showMore(clicked) {
      this.showItem = clicked;
      this.showMoreDialog = true;
    },
  },

  components: {
    Profile,
    Skills,
    Portfolio,
    PortfolioMoreDialog,
    Contact,
  },
};
</script>

<style lang="scss">
@import "@/assets/scss/import";
@import "@/assets/scss/reset";

.main {
  height: 500vh;
  line-height: 1.8;
  background: $main-background;
  text-align: left;

  &__container {
    margin: 0 auto 50px;
    transform: translateY(30px);
    opacity: 0;
    transition: 1s;

    @include mq("pc") {
      width: 84%;
      max-width: 1000px;
    }
    @include mq("tab") {
      width: 94%;
      max-width: 840px;
    }
    @include mq("sp") {
      width: 96%;
      max-width: 500px;
    }

    &.show {
      transform: translateY(0);
      opacity: 1;
    }

    @include mq("pc") {
      padding-top: 80px;
    }

    @include mq("sp") {
      padding-top: 30px;
    }

    &__title {
      display: flex;
      align-items: baseline;

      @include mq("pc") {
        margin-bottom: 50px;
      }

      @include mq("sp") {
        margin-bottom: 30px;
      }

      &--ja {
        &::before {
          margin-right: 6px;
          margin-left: 6px;
          content: "−";
        }
      }

      &--en {
        margin-right: 16px;
      }

      @include mq("pc") {
        &--en {
          font-size: 30px;
        }

        &--ja {
          font-size: 15px;
        }
      }

      @include mq("sp") {
        &--en {
          font-size: 22px;
        }

        &--ja {
          font-size: 12px;
        }
      }
    }

    &__content {
      display: block;
    }
  }
}
</style>
