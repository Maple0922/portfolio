<template>
  <section class="main__container portfolio" id="portfolio">
    <h2 class="main__container__title">
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
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/import";
</style>
