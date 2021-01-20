<template>
  <section class="main__container portfolio" id="portfolio">
    <h2 class="main__container__title" :class="{ show: show }">
      <p class="main__container__title--en">Portfolio</p>
      <p class="main__container__title--ja">制作実績</p>
    </h2>
  </section>
</template>

<script>
export default {
  name: "Portfolio",

  data() {
    return {
      show: false,
      portfolio: {
        practical: [
          {
            title: "as",
            description: "te",
          },
          {
            title: "as",
            description: "te",
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
        this.show = top < window.innerHeight - 100;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";
</style>
