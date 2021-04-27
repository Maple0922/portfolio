<template>
  <section class="main__container contact" id="contact" :class="{ show: show }">
    <h2 class="main__container__title">
      <p class="main__container__title--en">Contact</p>
      <p class="main__container__title--ja">お問い合わせ</p>
    </h2>
    <div class="main__container__content">
      <a
        href="https://github.com/Maple0922"
        class="main__container__content__link"
        target="_blank"
      >
        <component
          class="main__container__content__github"
          :is="'GithubBlackSvg'"
        />
      </a>
      <p class="main__container__content__message">
        お問い合わせはGithubに記載のメールアドレスよりお願い致します。
      </p>
    </div>
  </section>
</template>

<script>
import GithubBlackSvg from "@/assets/images/svg/github_black.svg";

export default {
  name: "Contact",
  data() {
    return {
      show: false,
    };
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll() {
      if (!this.show) {
        var top = this.$el.getBoundingClientRect().top;
        this.show = top < window.innerHeight - 150;
      }
    },
  },
  components: {
    GithubBlackSvg,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";

.main__container {
  &__content {
    padding: 40px 0;
    text-align: center;
    &__link {
      display: inline-block;
      margin-bottom: 32px;
      transition: 0.3s;

      @include mq("pc") {
        &:hover {
          opacity: 0.6;
        }
      }
    }
    &__github {
      @include mq("pc") {
        width: 64px;
        height: 64px;
      }

      @include mq("sp") {
        width: 48px;
        height: 48px;
      }
    }
    &__message {
      @include mq("pc") {
        padding: 0 12px;
        font-size: 15px;
      }

      @include mq("sp") {
        padding: 0 36px;
        font-size: 13px;
      }
    }
  }
}
</style>
