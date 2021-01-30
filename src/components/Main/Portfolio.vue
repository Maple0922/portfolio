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
      <template v-for="(item, key) in portfolio.personal">
        <PortfolioCard :portfolioItem="item" :key="key" @showMore="showMore" />
      </template>
    </div>
    <h3 class="main__container__subtitle">実務</h3>
    <div class="portfolio__wrapper practical">
      <template v-for="(item, key) in portfolio.practical">
        <PortfolioCard :portfolioItem="item" :key="key" @showMore="showMore" />
      </template>
    </div>
  </section>
</template>

<script>
import PortfolioCard from "@/components/Main/Portfolio/PortfolioCard.vue";

export default {
  name: "Portfolio",

  data() {
    return {
      show: false,
      showMoreDialog: false,
      portfolio: {
        personal: [
          {
            title: "ポートフォリオサイト",
            description: "自分のポートフォリオサイトです。",
            supplement:
              "アニメーションに絶対jQueryを使わないよう意識しました。",
            used: ["Vue.js"],
            image: "portfolio.png",
            github: "portfolio",
          },
          {
            title: "BUYO - 部室予約サイト",
            description:
              "自分の所属しているサークルで使う部室の利用時間予約サイトです。",
            supplement: "test",
            used: ["PHP", "SQLite"],
            image: "buyo.png",
            github: "ksre2",
          },
          {
            title: "TIME TABLE MAKER",
            description:
              "所属しているサークルのライブのタイムテーブルの作成し、時間を可視化できるサイトです。",
            supplement: "test",
            used: ["jQuery"],
            image: "time-table-maker.png",
            github: "time-table-maker",
          },
          {
            title: "Image PDF Converter",
            description: "画像をPDFに変換できるサイトです。",
            supplement: "test",
            used: ["PDFMake(ライブラリ)"],
            image: "image-pdf-converter.png",
            github: "image-pdf-converter",
          },
          {
            title: "oh-o!Meiji サーバーエラーbot",
            description:
              "大学のポータルサイトがエラーを起こした際にツイートでお知らせしてくれるbotです。",
            supplement: "test",
            used: ["PHP", "cron"],
            image: "server-error-bot.png",
            github: "time-table-maker",
          },
          {
            title: "Gamble Calculator",
            description:
              "友達と賭けでゲームをするときにポイント計算を効率よく行えるツールです。",
            supplement: "test",
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
            supplement: "test",
            used: ["Sass", "jQuery"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "社内ブログの枠組み実装",
            description:
              "社内の技術ブログの枠組みを、hugoという静的サイトジェネレータのテーマをカスタマイズして作りました。",
            supplement: "test",
            used: ["hugo"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "モバイルオーダーシステムのフロントエンド開発",
            description:
              "フロントにAngularを用いたシステムの実装、APIとの繋ぎ込みを行いました。",
            supplement: "test",
            used: ["Angular"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "新卒向け就活サービスの開発",
            description:
              "LPのコーディングからLaravelを用いた就活サービスの開発まで行いました。",
            supplement: "test",
            used: ["Laravel"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "大会運営者支援システムの開発",
            description:
              "トーナメント表の出力を始めとした、大会運営者向けの業務システムの開発を行いました。",
            supplement: "test",
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

    showMore(clickedItem) {
      this.$emit("showMore", clickedItem);
    },
  },

  components: {
    PortfolioCard,
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
}
</style>
