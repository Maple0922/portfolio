<template>
  <header class="header">
    <div class="header__container">
      <h1 class="header__title" :class="{ show: showTitle }">
        Futo Nakajima's Portfolio
      </h1>
      <p class="header__caption" :class="{ show: showCaption }">
        - Web Engineer -
      </p>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      showTitle: false,
      showCaption: false,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showTitle = true;
      setTimeout(() => {
        this.showCaption = true;
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

  &__title,
  &__caption {
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
      font-size: 16px;
    }
  }

  @include mq-header("tab") {
    height: $height-header-tab;

    &__title {
      font-size: 28px;
    }

    &__caption {
      font-size: 18px;
    }
  }

  @include mq-header("pc") {
    height: $height-header-pc;

    &__title {
      font-size: 36px;
    }

    &__caption {
      font-size: 20px;
    }
  }
}
</style>
