<template>
  <section
    class="main__container portfolio"
    id="portfolio"
    :class="{ show: show }"
  >
    <h2 class="main__container__title">
      <p class="main__container__title--en">Portfolio</p>
      <p class="main__container__title--ja">制作実績</p>
    </h2>
    <h3 class="main__container__subtitle">個人開発</h3>
    <div class="portfolio__wrapper personal">
      <div
        class="portfolio__container"
        v-for="(item, key) in portfolio.personal"
        :key="key"
      >
        <img
          class="portfolio__image"
          :src="require(`@/assets/images/photo/${item.image}.jpg`)"
          :alt="item.image"
        />
        <div class="portfolio__description">
          <h4 class="portfolio__description__title">{{ item.title }}</h4>
          <p class="portfolio__description__content">{{ item.description }}</p>
          <p class="portfolio__description__used">
            使用技術:
            <span
              class="portfolio__description__used__item"
              v-for="(tech, key) in item.used"
              :key="key"
              >{{ tech }}</span
            >
          </p>
        </div>
      </div>
    </div>
    <h3 class="main__container__subtitle">実務</h3>
    <div class="portfolio__wrapper practical">
      <div
        class="portfolio__container"
        v-for="(item, key) in portfolio.practical"
        :key="key"
      >
        <img
          class="portfolio__image"
          :src="require(`@/assets/images/photo/${item.image}.jpg`)"
          :alt="item.image"
        />
        <div class="portfolio__description">
          <h4 class="portfolio__description__title">{{ item.title }}</h4>
          <p class="portfolio__description__content">{{ item.description }}</p>
          <p class="portfolio__description__used">
            使用技術:
            <span
              class="portfolio__description__used__item"
              v-for="(tech, key) in item.used"
              :key="key"
              >{{ tech }}</span
            >
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Portfolio",

  data() {
    return {
      show: false,
      portfolio: {
        personal: [
          {
            title: "as",
            description: "te",
            used: ["tes", "tea", "ted"],
            image: "profile",
          },
          {
            title: "aws",
            description: "teaa",
            used: ["tefas", "taea", "teafd"],
            image: "profile2",
          },
          {
            title: "aas",
            description: "teh",
            used: ["tedfgds", "theda", "tehd"],
            image: "profile",
          },
        ],
        practical: [
          {
            title: "as",
            description: "te",
            used: ["tes", "tea", "ted"],
            image: "profile",
          },
          {
            title: "aws",
            description: "teaa",
            used: ["tefas", "taea", "teafd"],
            image: "profile2",
          },
          {
            title: "aas",
            description: "teh",
            used: ["tedfgds", "theda", "tehd"],
            image: "profile",
          },
        ],
      },
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
        this.show = top < window.innerHeight - 300;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";

.main__container__subtitle {
  font-size: 22px;
  padding-left: 20px;
  width: 100%;
  padding-bottom: 4px;
  margin-bottom: 16px;
}

.portfolio {
  &__wrapper {
    display: flex;
    flex-wrap: wrap;
  }

  &__container {
    width: calc(33.3% - 30px);
    background: transparentize($white, 0.4);
    border-radius: 4px;
    box-shadow: 0 1px 3px 0px $light-gray;
    height: 400px;
    margin: 0 15px 80px;
  }

  &__image {
    height: 240px;
    object-fit: cover;
    width: 100%;
    border-radius: 4px 4px 0 0;
  }

  &__description {
    padding: 0 20px 20px;
    &__title {
      font-size: 18px;
      font-weight: bold;
    }
    &__content {
      display: block;
    }
    &__used {
      font-size: 14px;

      &__item {
        display: inline-block;
        margin: 0 4px;
        padding: 2px 6px;
        background: $light-gray;
        border-radius: 4px;
        text-align: center;
      }
    }
  }
}
</style>
