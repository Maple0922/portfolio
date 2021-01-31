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
            supplement: [
              "Vue CLIで作りました。アニメーションに絶対jQueryを使わないよう意識しました。",
            ],
            used: ["Vue.js"],
            image: "portfolio.png",
            github: "portfolio",
          },
          {
            title: "BUYO - 部室予約サイト",
            description:
              "自分の所属しているサークルで使っている部室の利用時間予約サイトです。",
            supplement: [
              "今までメーリングリストにベタ書きでしていた予約作業を簡単に行えるようにするため作りました。",
              "手順を簡潔にすることに重点を置き、ログインを設けずに最低限のパスコードで使えるようにしました。",
              "予約･変更･削除時にはLINE、自分のSlackに通知が飛ぶようにし、ログが追えるようにしました。",
              "まだフレームワークを知らず、全て生のPHPで書きました。",
              "現在もサークル内で使われています。",
            ],
            used: ["PHP", "SQLite"],
            image: "buyo.png",
            github: "ksre2",
          },
          {
            title: "TIME TABLE MAKER",
            description:
              "所属しているサークルのライブのタイムテーブルの作成し、時間を可視化できるサイトです。",
            supplement: [
              "ライブ会場が電波の来ない地下にあり、オンラインで共有しても見れない人が多いため、簡単にタイムテーブルをその場で作成し掲示できるWebアプリを作りました。",
              "また、時間に合わせてタイムテーブル上をバーが動くため、演者のタイムキープにも役に立ちます。",
              "現在もサークル内で使われています。",
            ],
            used: ["jQuery"],
            image: "time-table-maker.png",
            github: "time-table-maker",
          },
          {
            title: "Image PDF Converter",
            description: "画像をPDFに変換できるサイトです。",
            supplement: [
              "大学のオンライン授業で「写真を撮ってPDFにして提出」という課題が増え、機械に弱い友達によく変換を頼まれていたので、1人でできるように作りました。",
            ],
            used: ["PDFMake(ライブラリ)"],
            image: "image-pdf-converter.png",
            github: "image-pdf-converter",
          },
          {
            title: "oh-o!Meiji サーバーエラーbot",
            description:
              "大学のポータルサイトがエラーを起こした際にツイートでお知らせしてくれるbotです。",
            supplement: [
              "オンライン授業の始まった年に大学のポータルサイトが頻繁にサーバー落ちするようになったため、スクレイピングでサーバー落ちを検知してお知らせするTwitter botを作りました。",
              "メンテナンス開始時、終了時にもお知らせします。",
              "このbotを作った直後にサーバーが強化され、全く落ちなくなりました。",
            ],
            used: ["PHP", "cron"],
            image: "server-error-bot.png",
            github: "time-table-maker",
          },
          {
            title: "Gamble Calculator",
            description:
              "友達と賭けでゲームをするときにポイント計算を効率よく行えるツールです。",
            supplement: [
              "ゲームの種類ごとに違うポイントや結果を、レートの調節や独自の評価基準で一元的なレベルのポイントに落とし込み計算できるようにしました。",
              "各ゲーム内での結果を入力すれば自動で計算し、各々の合計まで算出します。",
              "Vueの双方向データバインディングを活かしたWebアプリを作りたくなって作りました。",
            ],
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
            supplement: [],
            used: ["Sass", "jQuery"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "社内ブログの枠組み実装",
            description:
              "社内の技術ブログの枠組みを、hugoという静的サイトジェネレータのテーマをカスタマイズして作りました。",
            supplement: [""],
            used: ["hugo"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "モバイルオーダーシステムのフロントエンド開発",
            description:
              "フロントにAngularを用いたシステムの実装、APIとの繋ぎ込みを行いました。",
            supplement: [
              "初のチーム開発、中規模アプリの開発で、GithubとSlackを軸にしたフルリモートでの開発をここで経験しました。",
            ],
            used: ["Angular"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "新卒向け就活サービスの開発",
            description:
              "LPのコーディングからLaravelを用いた就活サービスの開発まで行いました。",
            supplement: [
              "Laravelでの基本的なMVCやCRUDの実装はここで学びました。",
            ],
            used: ["Laravel"],
            image: "cat.jpg",
            github: "",
          },
          {
            title: "大会運営者支援システムの開発",
            description:
              "トーナメント表の出力を始めとした、大会運営者向けの業務システムの開発を行いました。",
            supplement: [
              "LaravelでCRUDやマルチログイン、その他外部ライブラリなどを用いて独自の機能の実装をしました。",
            ],
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
