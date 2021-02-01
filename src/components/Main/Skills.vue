<template>
  <section class="main__container skills" id="skills" :class="{ show: show }">
    <h2 class="main__container__title">
      <p class="main__container__title--en">Skills</p>
      <p class="main__container__title--ja">スキル</p>
    </h2>
    <span class="caption">※太字下線は実務経験あり</span>
    <div class="skills__wrapper">
      <div
        class="skills__container"
        v-for="(skill, firstKey) in skills"
        :key="firstKey"
      >
        <h3 class="skills__category">{{ skill.category }}</h3>
        <ul class="skills__list">
          <li
            class="skills__list__item"
            v-for="(item, secondKey) in skill.items"
            :key="secondKey"
          >
            <p class="skills__list__item__name" :class="{ bold: item.ex }">
              {{ item.name }}
            </p>
            <p class="skills__list__item__stars">
              <component
                class="skills__list__item__star"
                v-for="n of item.star"
                :key="`n-index-${n}`"
                :is="'StarFillSvg'"
              />
              <component
                class="skills__list__item__star"
                v-for="m of 5 - item.star"
                :key="`m-index-${m}`"
                :is="'StarEmptySvg'"
              />
            </p>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script>
import StarFillSvg from "@/assets/images/svg/star_fill.svg";
import StarEmptySvg from "@/assets/images/svg/star_empty.svg";

export default {
  name: "Skills",
  data() {
    return {
      show: false,
      skills: [
        {
          category: "言語",
          items: [
            {
              name: "HTML5",
              star: 4,
              ex: true,
            },
            {
              name: "CSS3",
              star: 3,
              ex: true,
            },
            {
              name: "JavaScript",
              star: 3,
              ex: true,
            },
            {
              name: "PHP",
              star: 2,
              ex: true,
            },
          ],
        },
        {
          category: "フレームワーク･ライブラリ等",
          items: [
            {
              name: "Sass(SCSS)",
              star: 3,
              ex: true,
            },
            {
              name: "jQuery",
              star: 3,
              ex: true,
            },
            {
              name: "Vue.js",
              star: 3,
              ex: false,
            },
            {
              name: "Laravel",
              star: 3,
              ex: true,
            },
            {
              name: "React",
              star: 2,
              ex: false,
            },
            {
              name: "Angular",
              star: 1,
              ex: true,
            },
            {
              name: "node.js",
              star: 1,
              ex: false,
            },
          ],
        },
        {
          category: "開発ツール･DB等",
          items: [
            {
              name: "Git(Github)",
              star: 3,
              ex: true,
            },
            {
              name: "Webpack",
              star: 2,
              ex: true,
            },
            {
              name: "Wordpress",
              star: 2,
              ex: false,
            },
            {
              name: "MySQL",
              star: 2,
              ex: false,
            },
            {
              name: "SQLite",
              star: 2,
              ex: true,
            },
            {
              name: "GraphQL",
              star: 1,
              ex: false,
            },
          ],
        },
        {
          category: "その他ツール",
          items: [
            {
              name: "Figma",
              star: 3,
              ex: false,
            },
            {
              name: "Slack",
              star: 4,
              ex: true,
            },
            {
              name: "Chatwork",
              star: 3,
              ex: true,
            },
            {
              name: "Asana",
              star: 3,
              ex: true,
            },
            {
              name: "Trello",
              star: 3,
              ex: true,
            },
          ],
        },
      ],
    };
  },
  components: {
    StarFillSvg,
    StarEmptySvg,
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
.skills {
  .caption {
    font-size: 13px;
    margin-bottom: 16px;
    display: block;
    width: 100%;
    padding-right: 32px;
    text-align: right;
  }
  &__wrapper {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }

  &__container {
    background: transparentize($white, 0.4);
    border-radius: 4px;
    box-shadow: 0 1px 3px 0px $light-gray;
    padding: 20px 24px 24px;

    @include mq("pc") {
      width: calc(50% - 30px);
      margin: 0 15px;
      &:nth-child(-n + 2) {
        margin-bottom: 30px;
      }
    }
    @include mq("sp") {
      width: 100%;
      margin-bottom: 30px;
      max-width: 320px;
    }
  }

  &__category {
    display: block;
    margin-bottom: 16px;
    margin-left: 8px;
    @include mq("pc") {
      font-size: 18px;
    }
    @include mq("sp") {
      font-size: 16px;
    }
  }

  &__list {
    border-right: 1px solid $main-background;
    border-left: 1px solid $main-background;
    &__item {
      width: 100%;
      display: flex;
      align-items: center;
      border-top: 1px solid $super-light-gray;

      @include mq("pc") {
        font-size: 15px;
        padding: 10px 0;
      }

      @include mq("sp") {
        font-size: 12px;
        padding: 8px 0;
      }
      &:nth-child(2n-1) {
        // background: $light-gray;
        background: $main-background;
      }
      &:last-child {
        border-bottom: 1px solid $super-light-gray;
      }
      &__name {
        width: 50%;
        padding-left: 10px;

        &.bold {
          font-weight: bolder;
          text-decoration: underline;
        }
      }
      &__stars {
        display: flex;
        width: 50%;
        justify-content: flex-end;
        padding-right: 10px;
      }
      &__star {
        display: inline-block;
        margin-right: 3px;
        @include mq("pc") {
          width: 18px;
          height: 18px;
        }
        @include mq("sp") {
          width: 16px;
          height: 16px;
        }
      }
    }
  }
}
</style>
