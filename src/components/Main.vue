<template>
  <main class="main">
    <Profile />
    <Skills />
    <Portfolio />
    <Contact />
  </main>
</template>

<script>
import Profile from "@/components/Main/Profile.vue";
import Skills from "@/components/Main/Skills.vue";
import Portfolio from "@/components/Main/Portfolio.vue";
import Contact from "@/components/Main/Contact.vue";

export default {
  name: "Main",
  components: {
    Profile,
    Skills,
    Portfolio,
    Contact,
  },
};
</script>

<style lang="scss">
@import "@/assets/scss/import";

.main {
  height: 200vh;
  line-height: 1.8;
  background: $main-background;
  text-align: left;

  &__container {
    width: 84%;
    max-width: 1000px;
    margin: 0 auto 50px;

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
        margin-bottom: 80px;
      }

      @include mq("sp") {
        margin-bottom: 30px;
      }

      &--ja {
        &::before {
          margin-right: 6px;
          content: "−";
        }
      }

      &--en {
        margin-right: 16px;
      }

      @include mq("pc") {
        &--en {
          font-size: 28px;
        }

        &--ja {
          font-size: 16px;
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
