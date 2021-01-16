<template>
  <section class="main__container skills" id="skills">
    <h2 class="main__container__title">
      <p class="main__container__title--en">Skills</p>
      <p class="main__container__title--ja">スキル</p>
    </h2>
    <div class="skills__container" v-for="(skill, key) in skills" :key="key">
      <h3 class="skills__category">{{ skill.category }}</h3>
      <ul class="skills__list">
        <li
          class="skills__list__item"
          v-for="(item, key) in skill.items"
          :key="key"
        >
          {{ item.name }}
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
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
              star: 4,
              ex: true,
            },
            {
              name: "JavaScript",
              star: 4,
              ex: true,
            },
            {
              name: "PHP",
              star: 4,
              ex: true,
            },
          ],
        },
        {
          category: "フレームワーク",
          items: [
            {
              name: "Sass(SCSS)",
              star: 3,
              ex: false,
            },
            {
              name: "Vue.js",
              star: 3,
              ex: false,
            },
            {
              name: "jQuery",
              star: 3,
              ex: false,
            },
            {
              name: "Angular",
              star: 3,
              ex: false,
            },
            {
              name: "Laravel",
              star: 3,
              ex: false,
            },
          ],
        },
        {
          category: "ツール",
          items: [
            {
              name: "Git(Github)",
              star: 3,
              ex: false,
            },
            {
              name: "Gulp",
              star: 3,
              ex: false,
            },
            {
              name: "Webpack",
              star: 3,
              ex: false,
            },
            {
              name: "Wordpress",
              star: 3,
              ex: false,
            },
            {
              name: "MySQL",
              star: 3,
              ex: false,
            },
            {
              name: "SQLite",
              star: 3,
              ex: false,
            },
          ],
        },
        {
          category: "その他",
          items: [
            {
              name: "Atom",
              star: 3,
              ex: false,
            },
            {
              name: "Figma",
              star: 3,
              ex: false,
            },
            {
              name: "Slack",
              star: 3,
              ex: false,
            },
            {
              name: "Chatwork",
              star: 3,
              ex: false,
            },
            {
              name: "Asana",
              star: 3,
              ex: false,
            },
            {
              name: "Trello",
              star: 3,
              ex: false,
            },
            {
              name: "XSERVER",
              star: 3,
              ex: false,
            },
          ],
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";
.skills {
  &__container {
    display: block;
  }

  &__category {
    display: block;
  }

  &__list {
    &__item {
      display: inline-block;
      padding: 2px 8px;
      margin: 2px;
      font-size: 12px;
      color: $white;
      background: blue;
      border-radius: 8px;
    }
  }
}
</style>
