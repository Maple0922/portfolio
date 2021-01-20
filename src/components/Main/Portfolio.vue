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
          :src="require(`@/assets/images/photo/${item.image}`)"
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
          :src="require(`@/assets/images/photo/${item.image}`)"
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
            title: "ポートフォリオサイト",
            description: "自分のポートフォリオサイトです。",
            used: ["Vue.js"],
            image: "portfolio.png",
            github: "portfolio",
          },
          {
            title: "BUYO - 部室予約サイト",
            description:
              "自分の所属しているサークルで使う部室の利用時間予約サイトです。",
            used: ["PHP", "SQLite"],
            image: "buyo.png",
            github: "ksre2",
          },
          {
            title: "TIME TABLE MAKER",
            description:
              "所属しているサークルのライブのタイムテーブルの作成し、時間を可視化できるサイトです。",
            used: ["jQuery"],
            image: "time-table-maker.png",
            github: "time-table-maker",
          },
          {
            title: "Image PDF Converter",
            description: "画像をPDFに変換できるサイトです。",
            used: ["PDFMake(ライブラリ)"],
            image: "image-pdf-converter.png",
            github: "image-pdf-converter",
          },
          {
            title: "oh-o!Meiji サーバーエラーbot",
            description:
              "大学のポータルサイトがエラーを起こした際にツイートでお知らせしてくれるbotです。",
            used: ["PHP", "cron"],
            image: "cat.jpg",
            github: "time-table-maker",
          },
          {
            title: "Gamble Calculator",
            description:
              "友達と賭けでゲームをするときにポイント計算を効率よく行えるツールです。",
            used: ["Vue.js"],
            image: "vue-gamble-calculator.png",
            github: "vue-gamble-calculator",
          },
        ],
        practical: [
          {
            title: "toCサービスのLPコーディング",
            description:
              "デザインカンプを元に1枚のLPのコーディング、レスポンシブ対応を行いました。",
            used: ["Sass", "jQuery"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "社内ブログの枠組み実装",
            description:
              "社内の技術ブログの枠組みを、hugoという静的サイトジェネレータのテーマをカスタマイズして作りました。",
            used: ["hugo"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "モバイルオーダーシステムのフロントエンド開発",
            description:
              "フロントにAngularを用いたスマホ向けのシステムの実装、APIとの繋ぎ込みを行いました。",
            used: ["Angular"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "新卒向け就活サービスの開発",
            description:
              "LPのコーディングからLaravelを用いた就活サービスの開発まで行いました。",
            used: ["Laravel"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "大会運営者支援システムの開発",
            description:
              "トーナメント表の出力を始めとした、大会運営者向けの業務システムの開発を行いました。",
            used: ["Laravel"],
            image: "cat.jpg",
            github: "",
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
  width: 100%;
  text-align: center;
  padding-bottom: 4px;
  @include mq("pc") {
    margin-bottom: 32px;
    font-size: 22px;
  }
  @include mq("sp") {
    margin-bottom: 20px;
    font-size: 17px;
  }
}

.portfolio {
  &__wrapper {
    @include mq("pc") {
      display: flex;
      flex-wrap: wrap;
    }
  }

  &__container {
    background: transparentize($white, 0.4);
    border-radius: 4px;
    box-shadow: 0 1px 3px 0px $light-gray;
    height: 440px;
    cursor: pointer;
    @include mq("pc") {
      width: calc(33.3% - 30px);
      transition: 0.3s;
      margin: 0 15px 30px;
      &:hover {
        opacity: 0.6;
        transform: scale(1.03);
      }
      &:last-child {
        margin-bottom: 80px;
      }
    }
    @include mq("tab") {
      width: calc(50% - 30px);
    }
    @include mq("sp") {
      width: 100%;
      max-width: 400px;
      margin: 0 auto 30px;
    }
  }

  &__image {
    height: 240px;
    object-fit: cover;
    width: 100%;
    border-radius: 4px 4px 0 0;
    border-bottom: 1px solid $super-light-gray;
  }

  &__description {
    padding-bottom: 20px;
    &__title {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 10px;
      padding: 0 20px;
    }
    &__content {
      display: block;
      padding: 0 10px 10px;
      margin: 0 10px;
      margin-bottom: 10px;
      border-bottom: 1px solid $light-gray;
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 14px;
      }
    }
    &__used {
      padding: 0 20px;
      @include mq("pc") {
        font-size: 14px;
      }
      @include mq("sp") {
        font-size: 12px;
      }

      &__item {
        display: inline-block;
        margin: 0 4px;
        padding: 2px 6px;
        background: $super-light-gray;
        border-radius: 4px;
        text-align: center;
      }
    }
  }
}
</style>
