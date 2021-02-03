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
    <h3 class="portfolio__subtitle">個人</h3>
    <div class="portfolio__wrapper personal">
      <template v-for="(item, key) in portfolio.personal">
        <PortfolioCard :portfolioItem="item" :key="key" @showMore="showMore" />
      </template>
    </div>
    <h3 class="portfolio__subtitle">実務</h3>
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
            date: "2021-1",
            description: "自分のポートフォリオサイトです。",
            supplement: [
              "Vue CLIで作りました。アニメーションに絶対jQueryを使わないよう意識しました。",
            ],
            used: ["Vue.js"],
            thumbnail: "pf.png",
            images: ["pf.png", "pf.png", "pf.png"],
            github: "portfolio",
          },
          {
            title: "BUYO - 部室予約サイト",
            date: "2020-2",
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
            thumbnail: "by.png",
            images: ["by.png", "by.png", "by.png"],
            github: "ksre2",
          },
          {
            title: "TIME TABLE MAKER",
            date: "2020-4",
            description:
              "所属しているサークルのライブのタイムテーブルの作成をし、時間を可視化できるサイトです。",
            supplement: [
              "ライブ会場が電波の来ない地下にあり、オンラインで共有しても見れない人が多いため、簡単にタイムテーブルをその場で作成し掲示できるWebアプリを作りました。",
              "また、時間に合わせてタイムテーブル上をバーが動くため、演者のタイムキープにも役に立ちます。",
              "現在もサークル内で使われています。",
            ],
            used: ["jQuery"],
            thumbnail: "ttm.png",
            images: ["ttm.png", "ttm.png", "ttm.png"],
            github: "time-table-maker",
          },
          {
            title: "Image PDF Converter",
            date: "2020-4",
            description: "画像をPDFに変換できるサイトです。",
            supplement: [
              "大学のオンライン授業で「写真を撮ってPDFにして提出」という課題が増え、機械に弱い友達によく変換を頼まれていたので、1人でできるように作りました。",
            ],
            used: ["PDFMake"],
            thumbnail: "ipc.png",
            images: ["ipc.png", "ipc.png", "ipc.png"],
            github: "image-pdf-converter",
          },
          {
            title: "Oh-o!Meiji サーバーエラーbot",
            date: "2020-5",
            description:
              "大学のポータルサイトがエラーを起こした際にツイートでお知らせしてくれるbotです。",
            supplement: [
              "オンライン授業の始まった年に大学のポータルサイトが頻繁にサーバー落ちするようになったため、スクレイピングでサーバー落ちを検知してお知らせするTwitter botを作りました。",
              "メンテナンス開始時、終了時にもお知らせします。",
              "このbotを作った直後にサーバーが強化され、全く落ちなくなりました。",
            ],
            used: ["PHP", "cron"],
            thumbnail: "seb.png",
            images: ["seb.png", "seb.png", "seb.png"],
            github: "detect-error-bot",
          },
          {
            title: "Gamble Calculator",
            date: "2020-6",
            description:
              "友達と賭けでゲームをするときにポイント計算を効率よく行えるツールです。",
            supplement: [
              "ゲームの種類ごとに違うポイントや結果を、レートの調節や独自の評価基準で画一化し計算できるようにしました。",
              "各ゲーム内での結果を入力すれば自動で計算し、各々の合計まで算出します。",
              "Vueの双方向データバインディングを活かしたWebアプリを作りたくなって作りました。",
            ],
            used: ["Vue.js"],
            thumbnail: "vgc.png",
            images: ["vgc.png", "vgc.png", "vgc.png"],
            github: "vue-gamble-calculator",
          },
        ],
        practical: [
          {
            title: "toCサービスのLPコーディング",
            date: "2019-9",
            description:
              "デザインカンプを元に1枚のLPのコーディング、レスポンシブ対応を行いました。",
            supplement: [],
            used: ["Sass", "jQuery"],
            thumbnail: "lp.png",
            images: ["lp.png", "lp.png", "lp.png"],
          },
          {
            title: "社内ブログの枠組み実装",
            date: "2019-10",
            description:
              "社内の技術ブログの枠組みを、hugoという静的サイトジェネレータのテーマをカスタマイズして作りました。",
            supplement: [""],
            used: ["hugo"],
            thumbnail: "bl.png",
            images: ["bl.png", "bl.png", "bl.png"],
          },
          {
            title: "モバイルオーダーシステムのフロントエンド開発",
            date: "2020-1",
            description:
              "フロントにAngularを用いたシステムの実装、APIとの繋ぎ込みを行いました。",
            supplement: [
              "初のチーム開発、中規模アプリの開発で、GithubとSlackを軸にしたフルリモートでの開発を経験しました。",
            ],
            used: ["Angular"],
            thumbnail: "mos.png",
            images: ["mos.png", "mos.png", "mos.png"],
          },
          {
            title: "新卒向け就活サービスの開発",
            date: "2020-8",
            description:
              "LPのコーディングからLaravelを用いた就活サービスの開発まで行いました。",
            supplement: [
              "Laravelでの基本的なMVCやCRUDの実装はここで学びました。",
            ],
            used: ["Laravel"],
            thumbnail: "tc.png",
            images: ["tc.png", "tc.png", "tc.png"],
          },
          {
            title: "大会運営者支援システムの開発",
            date: "2020-11",
            description:
              "トーナメント表の出力を始めとした、大会運営者向けの業務システムの開発を行いました。",
            supplement: [
              "LaravelでCRUDやマルチログイン、その他外部ライブラリなどを用いて独自の機能の実装をしました。",
            ],
            used: ["Laravel"],
            thumbnail: "tw.png",
            images: ["tw.png", "tw.png", "tw.png"],
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
        this.show = top < window.innerHeight - 150;
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

.portfolio {
  &__subtitle {
    width: 120px;
    margin: 0 auto;
    text-align: center;
    padding-bottom: 4px;
    position: relative;
    &::before,
    &::after {
      content: "";
      position: absolute;
      display: inline-block;
      width: 30px;
      height: 1px;
    }
    @include mq("pc") {
      margin-bottom: 32px;
      font-size: 22px;
      &::before,
      &::after {
        top: 44%;
        border-top: 2px solid $light-gray;
      }
      &::before {
        left: 120px;
      }
      &::after {
        right: 120px;
      }
    }
    @include mq("tab") {
      font-size: 20px;
    }
    @include mq("sp") {
      margin-bottom: 10px;
      font-size: 16px;
      &::before,
      &::after {
        top: 40%;
        border-top: 1px solid $light-gray;
      }
      &::before {
        left: 100px;
      }
      &::after {
        right: 100px;
      }
    }
  }
  &__wrapper {
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 80px;
  }
}
</style>
